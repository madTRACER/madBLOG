---
title: 'EEPROM in STM32 using HAL'
description: 'I have never used internal EEPROM in STM32 before, and when I was needed to use it, I couldn’t find anything about usage of this peripheral. Anyway, I decided to write a simple how-to-start tutorial.'
date: '2019-02-17T18:04:34+06:00'
template: 'post'
draft: false
slug: 'eeprom-in-stm32-using-hal'
category: 'STM32'
tags: ['C++', 'STM32']
socialImage: '/media/2019-02-17--eeprom.png'
---
![](/media/2019-02-17--eeprom.png)

*This post is a translation from [Radiotech.kz](https://blog.radiotech.kz/stm32/eeprom-v-stm32l-s-ispolzovaniem-hal/)*

I have never used internal EEPROM in STM32 before, and when I was needed to use it, I couldn’t find anything about usage of this peripheral. Anyway, I decided to write a simple how-to-start tutorial.

First I need to say that I work with STM32L1 family MCU and all functions for working with it’s EEPROM are located in two files:

**stm32l1xx\_hal\_flash\_ex.c** and **stm32l1xx\_hal\_flash\_ex.h**

Before performing read/write operations with EEPROM it is needed to unlock access to the memory and **FLASH\_PECR** register. HAL has a special function for it:

```c++
HAL_FLASHEx_DATAEEPROM_Unlock (void);
```

You can find the description of **FLASH\_PECR** register on page 84 of [RM0038](https://www.st.com/content/ccc/resource/technical/document/reference_manual/cc/f9/93/b2/f0/82/42/57/CD00240193.pdf/files/CD00240193.pdf/jcr:content/translations/en.CD00240193.pdf) reference-manual.

If you are using memory address for the first time, you can write in instantly. Otherwise, you need firstly clear it before writing:

```c++
HAL_FLASHEx_DATAEEPROM_Erase (uint32_t TypeErase, uint32_t Address);
```

`TypeErase` – type of the variable, which need to be erased from EEPROM. This parameter can be set this values:

```c++
    #define FLASH_TYPEERASEDATA_BYTE         (0x00U)  // Erase 1 byte
    #define FLASH_TYPEERASEDATA_HALFWORD     (0x01U)  // Erase 2 bytes
    #define FLASH_TYPEERASEDATA_WORD         (0x02U)  // Erase 4 bytes
```

`Address` is an address in EEPROM memory. STM32L151 has 4096 bytes of EEPROM ranged from `0x08080000` to `0x08080FFF`.

If you look into HAL you can see that the function erases data by writing null in the given address of memory. Before erasing you first need to call `HAL_FLASHEx_DATAEEPROM_Unlock()` function. This step is also mandatory for other EEPROM working functions.

This function is used to write values in EEPROM:

```c++
HAL_FLASHEx_DATAEEPROM_Program (uint32_t TypeProgram, uint32_t Address, uint32_t Data);
```

`TypeProgram` – type of programming variable. This parameter can be set this values:

```c++
    #define FLASH_TYPEPROGRAMDATA_BYTE         (0x00U)  // Write 1 byte
    #define FLASH_TYPEPROGRAMDATA_HALFWORD     (0x01U)  // Write 2 bytes
    #define FLASH_TYPEPROGRAMDATA_WORD         (0x02U)  // Write 4 bytes
    #define FLASH_TYPEPROGRAMDATA_FASTBYTE     (0x04U)  // Write 1 byte in Fast mode
    #define FLASH_TYPEPROGRAMDATA_FASTHALFWORD (0x08U)  // Write 2 bytes in Fast mode
    #define FLASH_TYPEPROGRAMDATA_FASTWORD     (0x10U)  // Write 4 bytes in Fast mode
```

The difference between default and fast mode:

```c++
CLEAR_BIT(FLASH->PECR, FLASH_PECR_FTDW);
```

FTDW bit of FLASH\_PECR register controls data writing in fixed amount of time. If the bit cleared, a byte, half word or word is being written without erasing. Otherwise, a program will automatically erase data before writing. Therefore, writing will take 2xTprog amount of time.

The last EEPROM-working function:

```c++
HAL_FLASHEx_DATAEEPROM_Lock (void);
```

This function blocks access to EEPROM memory and **FLASH\_PECR** register.

I’ve written two simple EEPROM-working functions. Writing function:

```c++
    void writeToEEPROM (uint32_t address, uint32_t value)
    {
      HAL_StatusTypeDef flash_ok = HAL_ERROR;
      while (flash_ok != HAL_OK)
      {
        flash_ok = HAL_FLASHEx_DATAEEPROM_Unlock();
      }
      flash_ok = HAL_ERROR;
      while (flash_ok != HAL_OK)
      {
        flash_ok = HAL_FLASHEx_DATAEEPROM_Erase (FLASH_TYPEERASEDATA_WORD, address);
      }
      flash_ok = HAL_ERROR;
      while (flash_ok != HAL_OK)
      {
        flash_ok = HAL_FLASHEx_DATAEEPROM_Program (FLASH_TYPEPROGRAMDATA_WORD, address, value);
      }
      flash_ok = HAL_ERROR;
      while (flash_ok != HAL_OK)
      {
        flash_ok = HAL_FLASHEx_DATAEEPROM_Lock ();
      }
    }
```

Reading function looks similar to other reading functions:

```c++
    uint32_t readFromEEPROM (uint32_t address)
    {
      return (*(__IO uint32_t *)address);
    }
```

That is all basic information about EEPROM in STM32.
---
title: 'AVR Dragon on Linux'
description: 'Recently I was needed to make some project on Arduino. Unfortunately, given Arduino didn’t flash via UART using Bootloader properely (I don’t really know what happened with it), so I decided to flash it with ISP programmer.'
date: '2020-02-15T01:53:13+06:00'
template: 'post'
draft: false
slug: 'avr-dragon-on-linux'
category: 'Arduino'
tags: ['Arduino', 'C++', 'Linux']
socialImage: '/media/2020-02-15--avrdragon.png'
---
![](/media/2020-02-15--avrdragon.png)

Recently I was needed to make some project on Arduino. Unfortunately, given Arduino didn’t flash via UART using Bootloader properely (I don’t really know what happened with it), so I decided to flash it with ISP programmer.

I had AVR Dragon with me and didn’t want to buy another one (supported by Arduino IDE) because I don’t work with Atmel / Microchip MCUs. Thus, I started to search for the information about using AVR Dragon on Linux.

It was a little bit tricky to find anything useful about that, so I tried to merge all the given information and my own experience in this post.

Firstly, I used Arduino IDE to compile my code and export `.hex` file:

![](/media/2020-02-15--Screenshot-from-2020-02-14-14.33.29-1.png)

Exported file is located in the project / sketch folder.

Secondly, I connected my Arduino to AVR Dragon using ISP interface by the user guide recommendations. Of course, I also connected power supply to Arduino (I don’t recommend you to use AVR Dragon power pins because of high current value may be needed for your device).

Thirdly, I finally started flashing my device using this command in terminal:

```shell
avrdude -c dragon_isp -p atmega328p  -U flash:w:your_file_name.hex
```

Where `your_file_name` should be replaced with the name of `.hex` file.

Wait until the end of writing and checking of the firmware. Then, the work is done!!!

As you can see, `avrdude` natively supports AVR Dragon, so you don’t need to have Atmel Studio installed to use it.

I also found some information about debugging Arduino with AVR Dragon using Avarice and AVR GDB, but I wasn’t needed to debug. Maybe I will try it when I use Arduino or Atmel / Microchip MCUs next time in any project (hope, it will never happen 🙂 ).
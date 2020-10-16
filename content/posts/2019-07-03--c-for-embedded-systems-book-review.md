---
title: 'C For Embedded Systems book review'
description: 'I recently bought a new book written by Alex Tarasov aka @chrns which is called “C For Embedded Systems”. It will be useful for any person who wants to learn how to write code for MCU. Generally, many tricks are shown with STMicroelectronics ARM MCUs, but it is also useful for any others.'
date: '2019-07-03T23:57:15+06:00'
template: 'post'
draft: false
slug: 'c-for-embedded-systems-book-review'
category: 'Life'
tags: []
socialImage: '/media/2019-07-03--chrns_book.png'
---
![](/media/2019-07-03--chrns_book.png)

I recently bought a new book written by Alex Tarasov aka @chrns which is called “C For Embedded Systems”. It will be useful for any person who wants to learn how to write code for MCU. Generally, many tricks are shown with STMicroelectronics ARM MCUs, but it is also useful for any others.

The book is started with an introduction, where the author writes about history of micro controllers (first of them were used in space industry), basic information about ARM cores and architecture and abstraction levels used to simplify operations with thousands/millions of transistors.

Then it is written about information implementation in computing binary system based systems (any of CPUs, MCUs).

Next chapter tells about development instruments – Git, IDE, compilers etc.

4th chapter starts to describe main C futures, program structure, generic information about preprocessor, pointers, data types, structures, arrays, operators , loops, if/else, functions and other generic information about the language.

CMSIS and HAL are also described in this book via examples of code. CMSIS is written by ARM and compatible with all ARM based controllers. HAL is developed specially for STM MCUs and better oriented for them.

New STM32CubeIDE by Atollic and STMicroelectronics contains Atollic Truestudio IDE and STM32CubeMX – HAL code generator which helps to initialize and setup peripheral.

Recommendations about writing an effective code with special tips for developers and debug/testing process description is the best part of the book, IMHO.

The other half of the book is about programs architecture for different types of systems; linear, cyclic and RTOS program differences, interrupts, and tells many generic information about RTOS and programs for it.

Book also has very useful additional chapters about power consumption, lookup table, analog signals processing, communication protocols, fixed-point numbers computing, bootloader, and random numbers.

In conclusion, I can say that “C For Embedded Systems” is a great book for anyone who wants to start develop systems based on ARM micro controllers. It is good for hobbyists and professional developers, who wants to expand or refresh their knowledge.

Today, you can buy paperback or electronic version of the book in Russian. I hope that one day it will be translated into English to be available worldwide.
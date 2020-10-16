---
title: 'Hello Kernel Development'
description: 'Recently I’ve started to comprehend a grand area of system programming – **Linux Kernel Development**. As always, I’ve also started to find some materials about it.'
date: '2020-03-14T11:00:20+06:00'
template: 'post'
draft: false
slug: 'hello-kernel-development'
category: 'Linux Kernel'
tags: ['C', 'C++', 'Linux', 'Kernel']
socialImage: '/media/2020-03-14--hello-kernel.png'
---
![](/media/2020-03-14--hello-kernel.png)

Recently I’ve started to comprehend a grand area of system programming – **Linux Kernel Development**. As always, I’ve also started to find some materials about it. Unfortunately, this sphere is not very easy to be explained as I think, that is why it is really hard to find some course or book except classic one – *Linux Kernel Development* and more specific *Linux Device Drivers*. However, I continue find some unsystematized information that I would like to explain and save in the following series of articles about **Linux Kernel Development**.

This article will explain the general information about devices. We will also find out how to configure your development environment to start working on kernel modules. After setting up all the needed packages and settings, it will be shown how to write a simple “Hello World” module to learn the basics.

- - - - - -

### 1. Linux devices and modules basics 

Linux devices are divided into 3 types:

![](/media/2020-03-14--linux-devices.png)

- *Character* – r/w data by bytes (operates stream of bytes) – ex. serial port;
- *Block* – r/w data by blocks (operates blocks of data with fixed size) – ex. hard disk;
- *Network* – r/w data by packets (operates blocks of data with custom size) – any packet delivery based interface.

In kernel we have a special data structure called `struct device` that handles all calls of a particular module from the userspace. All devices are building a tree, so each device has a parent. They also have some private device data, type, mutex, kobject (file system sysfs), spinlock\_t, list of devices group, id, class and some other attributes that are in `struct device`.

![](/media/2020-03-14--kernel-app-inter.png)

Each kernel module works in kernel space but end user, particularly application developer needs to work with it from userspace. In Linux, drivers are represented as a special type of files so you can work with them from your app using standard file operations. Ex. `fopen("/dev/ttyS0/",)` that will call a `struct device` needed. Other methods are `fwrite()`, `fread()`, `fclose()`. Each file function call provides `syscall` which is handled by kernel module as an interrupt. `syscall` dispatcher analyzes register values and calls procedure that is linked to the operation.

The main instrument to debug kernel code is `printk` function. This function acts just like `printf` in apps. To filter debug messages according to their priority we use log levels given below:

```c
#define LOGLEVEL_DEFAULT		-1			// default (or last) loglevel
#define LOGLEVEL_EMERG			0			// system is unusable
#define LOGLEVEL_ALERT			1			// action must be taken immediately
#define LOGLEVEL_CRIT			2			// critical conditions
#define LOGLEVEL_ERR			3			// error conditions
#define LOGLEVEL_WARNING		4			// warning conditions
#define LOGLEVEL_NOTICE			5			// normal but significant condition
#define LOGLEVEL_INFO			6			// informational
#define LOGLEVEL_DEBUG			7			// debug-level message
```

You need to add `KERN` prefix with one of this suffixes to `printk` before the format string. Example:

```c
printk(KERN_INFO "Hello, loading");
```

We also have some neseccary terminal commands that we will use later:

- `lsmod` shows all kernel modules that are currently active
- `insmod` inserts module into kernel
- `less /var/log/syslog` to see system log
- `rmmod` removes module from kernel

  - - - - -


### 2. Development environment preparation 

First things first it is needed to install all required packages. In Ubuntu you can run the following command:

```shell
sudo apt-get install build-essential git libncurses5-dev bc 
```

I will not explain why we need each of them but you can always search for it if you don’t know it yet.

It is also important to have any text editor / IDE you want. For me I use **[VSCodium](http://vscodium.com/)** (free/open-source binaries of VS Code).

Then it is useful to clone the latest version of Linux Kernel source code (later you will use it as a reference):

```shell
wget <kernel-download-link> 
```

The latest `<kernel-download-link>` may be taken from *[kernel.org](https://www.kernel.org/)*. For today it is <https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.5.9.tar.xz>.

Unpack the archive you downloaded:

```sh
tar xf /<kernel-version>
```

- - - - - -

### 3. Hello World 

After all the things done we can start developing our first module that will say “Hello World” from kernel. Here is the source code of `hello.c`:

```c
#include<linux/module.h> // including the main header to develop modules

int init_module(void)
{
    printk( KERN_INFO "Hello world" );
    
    return 0;
}

void cleanup_module(void)
{
    printk( KERN_INFO "Leaving" );
}

MODULE_LICENSE("GPL"); // it is important to set license 
```

Hope the general structure of the code is clear for you. You can notice that we use `printk` to print some information.

We also need to create Makefile for `make` build tool:

```makefile
obj-m += hello.o

KERNEL_VERSION := $(shell uname -r)

KDIR ?= /lib/modules/$(KERNEL_VERSION)/build

all:
	$(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
	$(MAKE) -C $(KDIR) M=$(PWD) clean
```

After that you can build your module executing `make` command in the working directory via terminal.

Let’s get into some details of source code. `init_module` will be called when you run `insmod hello.ko`. Then you can check that your module is active with `lsmod | grep hello`. You can also see the debug messages provided by `printk` with `less /var/log/syslog`. After all you should remove your module from kernel with `rmmod hello`.

- - - - - -

You have learnt the basics of modules development and device types, configured environment for **Linux Kernel Development** and written a simple module for practice. If you like this article please share it with anybody interested in this topic. I will write more posts about **Linux Kernel Development** as soon as I will have information for you. Follow my [Telegram channel](https://t.me/madtracercom) whether you want to be informed about the latest updates in my blog.
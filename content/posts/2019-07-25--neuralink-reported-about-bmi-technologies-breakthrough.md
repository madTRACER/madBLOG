---
title: 'Neuralink has reported about BMI technologies breakthrough'
description: 'A few days ago (July, 16th) Neuralink team presented their progress for the last 2 years in their field of development – Brain-Machine Interfaces. They told about main futures and technologies for all people who are interested in this project.'
date: '2019-07-25T02:54:37+06:00'
template: 'post'
draft: false
slug: 'neuralink-reported-about-bmi-technologies-breakthrough'
category: 'Life'
tags: []
socialImage: '/media/2019-07-25--neuralink.png'
---
![](/media/2019-07-25--neuralink.png)

A few days ago (July, 16th) Neuralink team presented their progress for the last 2 years in their field of development – Brain-Machine Interfaces. They told about main futures and technologies for all people who are interested in this project. Many news websites have already reviewed the [presentation](https://www.youtube.com/watch?v=r-vbh3t7WVI&feature=youtu.be), but this presentation is focused on recruiting specialists from different fields of study connected with Neuralink products so they presented only general information about the project.

Two days later Neuralink team uploaded a paper called [“An integrated brain-machine interface platform with thousands of channels”](https://www.biorxiv.org/content/10.1101/703801v2). This review will be generally based on this paper with some pictures from the presentation.

The main goal of Neuralink is to create a simple-mounted brain machine interface that can be inserted without pain and bleed and control all regions of cortex. This device will give us a way to solve brain and spinal cord problems or to control artificial body parts. On the other hand we will be able to create a super intelligence by merging our brain with AI.

Now I want to move closer to the technical details of the project, because I’m an engineer (not a journalist). If you want to read a simple review you can search Google 🙂

**Introduction**

![](/media/2019-07-25--neuralink-2.png)According to the previous researches, BMI is a great technology to control devices by our brain. It has already been demonstrated brain control of computer cursors, robotic limbs, speech synthesizers using only less than 256 electrodes. We have invasive BMI examples that are developed for a specific purpose, but they are not good in precision because one electrode controls millions of neurons. Moreover, they are difficult to insert because of very dangerous surgery needed. On the other hand, we have noninvasive approach, but they are very low accurate because of noises, also low density of electrodes. Therefore, it was needed to create very small electrodes which will be easy to insert without any harm or bleed.

Most of exist electrodes are made from rigid metals or semiconductors. They are not fully bio-compatible and have fixed-geometry and big size. The other approach is to use polymer films. They don’t have all weaknesses of semiconductor based electrodes, but it is very hard to mount them.

Therefore, it was needed to create ultra-fine polymer probes, a neurosurgical robot and high-density electronics.

**Threads**

![](/media/2019-07-25--neuralink-3.png)

![](/media/2019-07-25--neuralink-4.png)

![](/media/2019-07-25--neuralink-5.png)

The probes are made from polyimide (fully bio-compatible material) , which encapsulates gold traces. Each film array contains “thread” zone that futures an electrode contacts and “sensor” area that connects the electrodes with electronics. This thin films are patterned on a wafer with 3,072 electrode contacts for 32 independent electrodes. Each array has 48 or 96 threads.

According to this information each thread has to be connected to the electronic chip by 3072 contacts. to increase the safety and decrease the needed area Neuralink uses [flip-chip bounding method](https://en.wikipedia.org/wiki/Flip_chip). This method is using [stepper lithography](https://en.wikipedia.org/wiki/Stepper) and other microfabrication techniques to create sub-micron metal films.

Each thread has 4-6 μm thickness that includes up to 3 layers of insulation and 2 conduction layers. Typical length of the thread is about 20 mm. Parylene-c is deposited onto the threads to create a film that will safe them until they will be pulled of by the surgical robot. Each thread ends in a (16 × 50) μm<sup>2</sup> loop for needle threading.

Since the individual gold electrode has a very small surface area Neuralink decided to use special electrically conducive polymer poly-ethylenedioxythiophene doped with polystyrene sulfonate (PEDOT:PSS) and iridium oxide (IrOx) to increase the charge-carrying capacity and decrease the impedance. According to the information from the experiments, they achieved impedances of 36.97 ± 4.68 kΩ (*n* = 257 electrodes) and 56.46 ± 7.10 kΩ (*n* = 588) for PEDOT:PSS and IrOx, respectively. As you can see, PEDOT:PSS has lower impedance, but it can be less long-term stable and bio-compatible than IrOx. They are still working on the improvement of this techniques and planning to test other materials in the future.

**Robot**

![](/media/2019-07-25--neuralink-6.jpg)

The robotic electrode inserter; enlarged view of the inserter-head shown in the inset. **A.** Loaded needle pincher cartridge. **B.** Low-force contact brain position sensor. **C.** Light modules with multiple independent wavelengths. **D.** Needle motor. **E.** One of four cameras focused on the needle during insertion. **F.** Camera with wide angle view of surgical field. **G.** Stereoscopic cameras.

![](/media/2019-07-25--neuralink-7.jpg)

Needle pincher cartridge (NPC) compared with a penny for scale. **A.** Needle. **B.** Pincher. **C.** Cartridge.

Thin films are very good for insertion in our brain cortex, but they are extremely small that makes implantation process very complicated for surgeons. That is why Neuralink was needed to develop a robot that will insert this films into human’s brain. The robot’s insertion head is mounted on 10 μm globally accurate, 400 mm 400 mm 150 mm travel three-axis stage, and holds a small, quick-swappable, NPC (Needle pincher cartridge).

The needle is milled from 40 μm diameter tungsten-rhenium wire-stock electrochemically etched to 24 μm diameter along the inserted length. It is designed both to transferring and inserting threads and to penetrate the brain tissue. The needle is controlled by linear motor with very high speed and rapid retraction acceleration to separate the thread after insertion. Pincher is made from 50 μm tungsten wire bent at the tip. It is driven rotationally and axially to support probes and set them along the needle path.

Robot’s head also has a special imaging stack for the insertion control. It additionally contains 6 light modules. 405 nm illuminates fluorescence of polyimide to localize a thread loop for computer vision. 650 nm light illuminates the needle to control it. 525 nm light allows to precise the location of cortical surface.

A special software pre-select insertion paths and sites to choose the best way for threads. One of the advantages is the ability to avoid vasculature during a surgery. It is particularly important in BMI implantation as blood-brain barrier damage is one of the main causes of response of human body to foreign objects.

Robot has an auto-insertion mode in that it can insert up to 6 threads (192 electrodes) per minute. Despite surgery is automated, surgeon can easily adjust the position of thread. Robot also uses ultrasonic cleaning to sterilize the needle before insertion. Moreover, NPC can be easily replaced.

 The experiments showed the 87.1 ± 12.6 % success of insertion. It means that this robot can be used to insert large numbers of electrodes.

**Electronics**

![](/media/2019-07-25--neuralink-8.png)

![](/media/2019-07-25--neuralink-9.png)

![](/media/2019-07-25--neuralink-10.png)

![](/media/2019-07-25--neuralink-11.png)

The conditions inside the brain request the small size electronic device that needs to record and amplify and digitalize low-voltage neural signals (&lt;10 μV), filter all out-of-band noise and stream the signals out. Neuralink electronics is based on ASIC – application specific integrated circuit that consists of 256 programmable amplifiers called “analog pixels”, ADCs (analog to digital converters) and special module for signals serialization. Each analog pixel can be individually configured according to brain signals properties. ADCs work at 19.3 kHz frequency with 10 bit resolution. One analog pixel consumes 5.2 μW, while the ASIC consumes ~6 mW including clocks. In the main electronics system some ASICs are integrated in one PCB using flip-chip method. Today, each sensor contains an FPGA (field-programmable gate array) real-time temperature, accelerometer, and magnetometer sensors; and a USB-C connector for data transfer. The systems have titanium packages protected by parylene-c.

The basic station that can support up to 3 implants simultaneously converts data to UDP packages and sends in via 10G Ethernet anywhere it is needed.

**Conclusion**

![](/media/2019-07-25--neuralink-12.png)

![](/media/2019-07-25--neuralink-13.png)

As you could understand from the given information, Neuralink has already developed a special technologies that can be used to create a special BMI to make a make a Matrix scenes available in real life. As Elon Musk and his team said they are planning to create a simple mounted device that will upgrade our brain with AI, make prostheses easily controlled by humans brain. Moreover, they ensured us the ability to modernize cognitive part of our brain via sending some information into the brain. As a joke or small addition, Elon said that this Neuralink will also be a good controller for game characters 🙂

P.S. An additional information and links are given below the [original paper.](https://www.biorxiv.org/content/10.1101/703801v2)

*The information about Neuralink technologies, experimental data and pictures were taken from official resources:*

- [*https://www.neuralink.com/* ](https://www.neuralink.com/%20)
- [*https://www.biorxiv.org/content/10.1101/703801v2*](https://www.biorxiv.org/content/10.1101/703801v2)
- [*https://www.youtube.com/watch?v=r-vbh3t7WVI&amp;feature=youtu.be*](https://www.youtube.com/watch?v=r-vbh3t7WVI&feature=youtu.be)
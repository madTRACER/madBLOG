---
title: 'madEEG - Introduction'
description: 'A few months ago I’ve posted about Neuralink project where people want to create a new level BMI (Brain Machine Interface). I became really interested and started to think about something simpler to try brain activity analysis at home.'
date: '2020-01-14T04:13:19+06:00'
template: 'post'
draft: false
slug: 'madeeg-introduction'
category: 'Portfolio'
tags: ['madEEG']
socialImage: '/media/2020-01-14--madEEG_intro.png'
---
![](/media/2020-01-14--madEEG_intro.png)

A few months ago I’ve posted about [Neuralink project](http://madtracer.com/live/neuralink-reported-about-bmi-technologies-breakthrough/) where people want to create a new level BMI (Brain Machine Interface). I became really interested and started to think about something simpler to try brain activity analysis at home.

As it was told in the Neuralink presentation, we have noninvasive traditional method called EEG (Electroencephalography). This method is generally used to detect different neural diseases but it is also suitable for simple BMI implementation (as we will see later).

The main problem of EEG devices is their price. They cost about $1000 and more because of special certification needed. That is why I decided to look through the methods principals and structure of the devices.

EEG is a noninvasive method of bioelectrical brain activity registration. Brain activity can be defined by small intensity (uV) signals with some ranges of oscillations frequency and voltage amplitude.

![](/media/2020-01-14--madEEG_intro_1.png)

As you can see on the picture below there are 5 general ranges:

- **Gamma** *(&gt;30 Hz, 10-15 uV)* – registered during processes with high level of concentration.
- **Beta** *(14-40 Hz, 3-7 uV)* – typical rhythm for people when they have their eyes open.
- **Alpha** *(8-13 Hz, 5-100 uV)* – the highest amplitude can be registered when eyes closed.
- **Theta** *(4-8 Hz, 20-100 uV)* – points on a “sleepy” person who is between sleeping and awaking.
- **Delta** *(1-4 Hz, 20-200 uV)* – this rhythm is characteristic of sleeping process.

And some specific:

- **Kappa** *(8-13 Hz, 5-40 uV)* – similar with alpha rhythm, but oscillations are fusiform. Registered during intensive thought.
- **Mu** *(8-13 Hz, &lt;50 uV)* – also similar with alpha rhythm, but oscillations have a form of an arch. Connected with tactile feelings and moving imagination.
- **Tau** *(8-13 Hz)* – detected during sound activity.

As you can see, we have a lot of different signals from our brain that can be captured by EEG devices. Moreover, all of the needed frequencies are between 1 and 35 Hz so we need to filter them to prevent any other frequencies from our signals.

Lets get closer to the analog part of my **madEEG** device (which I’ve already started to develop 🙂 ) and review all the steps needed in the next post soon…
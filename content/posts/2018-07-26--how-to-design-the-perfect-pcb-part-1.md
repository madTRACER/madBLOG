---
title: 'How To Design the Perfect PCB. Part 1'
description: 'This post is the first in a two part series about designing the perfect printed circuit board (PCB). This part focuses on the pre-layout details that may be more important than you realize. The second part focuses more on the actual PCB layout and post-layout considerations.'
date: '2018-07-26T18:30:31+06:00'
template: 'post'
draft: false
slug: 'how-to-design-the-perfect-pcb-part-1'
category: 'Hardware'
tags: ['Hardware', 'PCB']
socialImage: '/media/2018-07-26--perfect-pcb-1.jpg'
---
![](/media/2018-07-26--perfect-pcb-1.jpg)

This post is the first in a two part series about designing the perfect printed circuit board (PCB). This part focuses on the pre-layout details that may be more important than you realize. The second part focuses more on the actual PCB layout and post-layout considerations.

### Step 1: How To Design the Perfect PCB

**This post is the first in a two part series about designing the perfect printed circuit board (PCB). This part focuses on the pre-layout details that may be more important than you realize. The second part focuses more on the actual PCB layout and post-layout considerations.**


Breadboards are amazing for prototyping and are an invaluable tool to any electronics tinkerer, but when you really want to get serious you will need to learn how to create your own PCB.

Making a PCB is no simple task, however, with the right commitment, a little bit of time, and this guide you will be able to make a working PCB the first time around. If you are persistent it will even look good!

#### Anatomy of a PCB

When you are on your computer, everything is at kind of an abstract level and it can be easy to forget that you are working with a physical medium. Before you just start throwing together a design, I think it is useful to know what you are actually doing.

If you are already fairly familiar with PCBs then you can skip to the good stuffs.

#### Board Materials

First we should understand what materials go into a PCB. At the most basic level, the base of the PCB is formed out of some sort of solid, non-conductive, material. This material is then laminated with a copper (or other metal) sheet, this creates the conductive surface.

The base material is usually a type of glass-reinforced epoxy known as FR-4. This is the most common material because it is flame resistant, cheap, and of course has a low conductivity.

For higher performance circuits (RF), there are other types of materials to consider such as ceramic or PTFE bases with various fillers. Since this article is more focused on general PCB design I will not go into details about designing for RF. Fortunately the EDN Network has posted a useful article on choosing PCB materials for high frequency circuits.

Really these two materials are about all that goes into a bare PCB. When you send your design for manufacture (or do it yourself) the electrical connections are usually created by removing select copper portions of the bare PCB.

#### Layers

The **cheapest PCBs are single sided boards**. This means that they are just made of the base material, with a single sheet of metal over the top.

Single sided boards are incredibly easy to work with, if you are making your own PCB at home you will most likely be designing for a single sided board.

While the single sided boards are simple to manufacture and understand, they can also be a pain when laying out your PCB. Since you only have one layer of metal to work with, you cannot cross electrical connections without the help of some external jumper.

As a result of this complication the majority of simple commercial and hobbyist boards are created on double sided PCBs. On a double sided PCB it is a simple matter to cross electrical connections and this fact allows for more complex yet elegant designs.

For all but the simplest of designs **I recommend designing for a double sided PCB**. This is generally the most cost effective method that will leave you with the least headache possible.

As designs become even more complex, it may even become necessary to add additional layers to your design. This can be useful if your board has incredibly complex signal paths or if you are aiming for a compact design.

**For the majority of users I do not recommend using more than two layers**, if you do this and do not need to you will end up with an unnecessarily complex design that will cost more to produce.

#### Copper Traces

The copper traces on your PCB are easily the most important part of the design so it is important to understand what they’re doing and what limitations you should consider.

As I mentioned earlier, copper traces are created by removing copper from the solid sheet that sits on top of the base material.

This means that the traces on your board are in fact just thin layers of copper. I don’t know about you, but when I discovered that it came as a bit of a surprise (relax I didn’t just find this out). For the longest time I assumed that PCBs were manufactured by pouring copper into a mold, letting it cool, and then somehow melting an insulator around the copper.

The thin sheet nature of these traces mean that there are some constraints to consider when routing your traces, most importantly, size considerations. All of these nuances will be discussed in detail in part 2.

#### Vias

The final “main component” of a PCB would be the ever useful via. Vias are used in multi-layer boards to electrically connect one layer to another.

There are essentially three types of vias, only one of which is common in the hobbyist world. These via types are:

- **Through hole** – Most common type of via, a hole is drilled through the whole board and then electroplated so that it is conductive.
- **Blind** – A blind via is used in designs with more than two layers to connect a surface layer to an internal layer without going all the way through.
- **Buried** – Buried vias are similar to blind vias but are only used to connect internal layers.

#### Other Things

After discussing PCB materials, possible layering options, copper traces, and vias we have pretty much covered the basics for what makes a PCB what it is. Understanding these things certainly gives you enough information to make your own working design, but there are still some other concepts to consider.

Some other PCB concepts to explore:

- **Soldermask** – If I had to guess what you think of when I say “PCB” I would bet that it is probably something green. Did you know that PCB’s are not this color as a result of what material is used? This is in fact another layer that is applied to the board after manufacturing. The purpose is to keep solder paste from spreading where it shouldn’t be, but it also has the effect of giving the board a definite style.
- **Fiducials** – These are special markings on your board that allow a pick-and-place automated assembly machine to calibrate itself. Fiducials are usually just a circle where the soldermask has not been applied with copper circle in the middle. This makes the point appear fairly reflective.
- **Silkscreen** – This is also another layer of the PCB added after fabrication. Silkscreen is used to provide visual cues to the user, document board information, identify proper component placement, or for branding. There are conflicting suggestions on proper usage of silkscreen and I will address this in part 2.
- **Copper fill** – Deciding whether to use a ground/power plane in your design will be an important decision to make during the design stage. The most common reasons for using a copper fill are to suppress noise on the ground circuitry, dissipate heat from a particularly active device, or because someone told you that was the way to do it.

That’s enough of learning what goes into PCBs though, let’s discuss how to get started on your design.

### Designing Your Circuit

Before you can consider any physical designs or schematic connections **you must have a clear idea of what you want your design to do**. This means taking some time to sit down and define what you want to accomplish, consider the challenges, and pick the right components for the job.

#### Determining Your Goals

**The first step in designing the perfect PCB is to have a well-defined set of goals** that you would like your design to accomplish. To steal a little bit from the business world, you should always set SMART goals for your project, this means:

- Specific
- Measurable
- Attainable
- Realistic
- Time Bound

As a personal example, I have started working on another side project for my own use. The bathroom in my apartment is too dark in the evening for me to get around in, but when I turn the light on it is way too bright and wakes me up.

To fix this little issue I thought I would just go buy a small lamp. Unfortunately, I am a little bit too picky and couldn’t find a lamp that I liked. That is when I had the idea to design one of my own. Of course, I’m not talking about just any lamp. I wanted a multi-color, adjustable brightness, wirelessly controlled lamp.

Sounds cool right? Of course it does! So before the idea was able to leave my head I jotted it down in my notebook and began planning.

At this point, my goals were pretty broad, let’s take a look at what I had:

- Multi-color lamp
- Adjustable brightness
- Wireless control

Unfortunately none of these goals are very specific at all. What do I mean by multi-color? Is that two colors, three, or any variable color? What is adjustable brightness? I mean technically on and off would be two different brightness settings right? Wireless control? What, do I want to use Wi-Fi, Bluetooth, infrared, RF, Zigbee, sound? Any of these options would be possible.

Revising the project goals to be SMART led me to the following list of goals:

- A continuously adjustable high-brightness RGB LED filtered through a fogged acrylic cover for even light dispersal.
- Continuously variable brightness control that will allow me to choose any brightness setting between completely off and fully on.
- Bluetooth low energy 4.0 wireless specification interface, controllable from an iOS or Android devices as well as an optional dedicated controller.

With the exception of “time bound” these goals meet all of the criteria of a SMART design and allow me to proceed forward with a clear vision of what I want to accomplish.

**By doing your research first and setting SMART goals for your project you place yourself on the right track to create that perfect design.**

#### Visualizing Your Design

Now that you have a clear idea of what you want, it is time to start designing it. Before you start scouring the internet for parts or drawing crazy schematics in your notebook, I would advise you to **take some time to develop a clear picture of how you want your final design to function**.

Try to determine how your parts will work together to achieve the goals you set. **This is a good time to be thinking about your design from a system level.**

You may not know specifics like what supply voltages you will need or what connections need to be made, but you will be able to consider how each component will rely on the others and what additional components they will add to your design.

**This is also a good time to consider the aesthetic aspect of your design.** Are you trying to fit a certain form factor? Do you need to consider ergonomics (for example if you are designing a game controller)? Will you be able to pick up your design a year from now and understand exactly how it works? These are the types of details that, while seemingly insignificant, can be the difference between a good design and a great design.

I know all this talk of visualization may sound cheesy and like it won’t really get you anywhere, but I assure you it is worthwhile. If you don’t want to believe me, consider this quote from Nikola Tesla’s autobiography where he describes his creative process:

> My method is different. I do not rush into actual work. When I get an idea I start at once building it up in my imagination. I change the construction, make improvements and operate the device in my mind. It is absolutely immaterial to me whether I run my turbine in thought or test it in my shop. I even note if it is out of balance. There is no difference whatever, the results are the same.

Of course the vast majority of us aren’t at the level of crazed genius that is Tesla, but the idea behind this method is all the same. **By visualizing your design beforehand you save time, money, and frustration**.

#### Choosing Parts

This is perhaps the most tedious step in the design process, but is crucial to a successful design. **Choosing the right part for your design could be the difference between finishing your project and giving up in frustration**.

All integrated circuit manufacturers work hard to make their designs robust and perform their function at the lowest price they can, but not all companies are equal. This is especially true when it comes to making their parts easy to use.

Since there are hundreds of thousands (millions?) of different components on the market, it isn’t possible for me to give a complete rundown, but what I can do is provide some general guidance on how to select the best component for your purpose.

1. **Check availability**. The last thing you want to do is put weeks or months into a design only to find out when you go to buy your parts that a crucial component is out of stock and will not be available for a few more months. Choose a part that shows a large inventory and optimally is available from multiple distributors.
2. **Consider where the component is in the product** **life-cycle**. You generally don’t want to get a component that is no longer in active production, but if your project is just a one-off build then this may not be a big deal.
3. **Make good use of the parts filters.** Most distributors or part finding tools offer some way to narrow your search criteria. Make use of this not only to reduce the amount of parts you have to look at but also as suggestions for alternative components. As a simple example let’s assume you have decided you want an LED with a millicandela rating of at least 80 mcd. Instead of filtering for components that have a rating of exactly 80 mcd, filter for any component with at least 80 mcd then sort by price, forward voltage drop, or current draw. This method may save you money while also getting you a better performing component.
4. **Be aware of minimum quantities.** Some components are only sold in large lots, be aware of this when choosing your components so that you aren’t forced to do a redesign.
5. **Know what package you are getting.** All components are delivered in some type of package that allows you to attach them to your board. Some components are offered in multiple package styles that are usually incompatible. If you are planning on making your PCB at home you should try to avoid the very small packages such as no-lead packages or chip-scale packages. These can be difficult to solder without proper equipment.
6. **Understand the part!** This is the final and most important guideline that I have. You should always fully understand the part before deciding to use it in your project. Some components can require a microcontroller or microprocessor, an external clock, or a special PCB design. Being aware of these requirements beforehand will help you avoid headaches in the future.

When it comes to actually finding parts, I like to use the search capabilities provided by my favorite vendors, this way I know the product will be available and I can choose components based on the actual cost to me and available inventory.

Another way to search for parts would be to go to a particular company’s website and browse their parts catalog for a solution. For example, if I know I need an ADC for a project, I may start with a company that is well-known for their ADC products such as TI. This has the advantage of often leading to a highly usable solution.

**This is just my preference, do you have a better method of finding parts? Let me know in the comments below.**

#### Sketching Your Connections

The final step before we switch over to software is to get a “first draft” of your design onto paper. Nikola Tesla would not approve, but he’s not around to stop you so don’t worry. This is a good way to get the specifics of your project organized in a coherent manner. I like to separate each system level block on a new page.

I also think it is useful to make a note here of what each important pin on the component does. It probably wouldn’t hurt to get started on your bill of materials as well, this may change as your design evolves, but it at least serves as a good starting point.

In addition to the basic information, you may also want to include some more detailed info about the part that you think may be important. For example, it may become tedious to refer back to the datasheet for I2C address information or possible pin configurations, these are good details to include in your notebook.

*For sketching my designs, both electrical and mechanical, I like to use any notebook for sketches and planners such as Trello to make my goals.*

After you have finished sketching your design, you have completed all of the pre-layout checks and are ready to move on to the physical design of your PCB.

**Now that you know what needs to be done to plan for your design, you can move on to part 2 in this series**

*Materials for this article were copied from [here](https://www.pcbway.com/project/share/How_To_Design_the_Perfect_PCB___Part_1.html) with some additions and changes*
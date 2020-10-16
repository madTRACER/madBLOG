---
title: 'How to Design the Perfect PCB – Part 2'
description: 'This post continues from “How to Design the Perfect PCB – Part 1.” In part one we covered how to finish the pre-layout work like setting goals, visualizing your design, and selecting parts. In this post we focus more on the physical side of PCB design and discuss the caveats that may trip you up.'
date: '2018-07-26T19:11:57+06:00'
template: 'post'
draft: false
slug: 'how-to-design-the-perfect-pcb-part-2'
category: 'Hardware'
tags: ['Hardware', 'PCB']
socialImage: '/media/2018-07-26--perfect-pcb-2.jpg'
---
![](/media/2018-07-26--perfect-pcb-2.jpg)

This post continues from “How to Design the Perfect PCB – Part 1.” In part one we covered how to finish the pre-layout work like setting goals, visualizing your design, and selecting parts. In this post we focus more on the physical side of PCB design and discuss the caveats that may trip you up.

#### Step 1: How to Design the Perfect PCB

This post continues from “How to Design the Perfect PCB – Part 1.” In part one we covered how to finish the pre-layout work like setting goals, visualizing your design, and selecting parts. In this post we focus more on the physical side of PCB design and discuss the caveats that may trip you up.

Before we get started, I think it is worth saying that this is NOT a guide on how to use any specific CAD software. This article is meant to serve as a general guideline on how you can design the best possible PCB regardless of your experience level.

When I set out to design my first PCB I was told “Well, it’s your first PCB so it probably won’t work anyways, but that sounds interesting.” Even though this was discouraging to hear, I didn’t let it stop me and I ended up with a working design. I now want to take my experiences as well as the experiences of others and make it as simple as possible for you to design your own PCB.

Putting the Design into Software
--------------------------------

Now that you have an idea of how you want the project to turn out, it’s time to start moving the design onto your computer

#### Choosing a CAD Package

The first step is to choose what CAD package you will be using in order to design your PCB. There are a dizzying amount of options on the market and I don’t know that I can even attempt to list them all, but here are some of your options:

- EAGLE (Free with limitations, upgrades from $70 – $1640)- A powerhouse in the hobbyist world, EAGLE probably has the most community support, but has some quirks that led me to choose a different suite.
- KiCad (Free and open source, no limitations) – This is my current personal favorite. As a FOSS option that is quite capable, you have nothing to lose by trying it out. I think it is better than EAGLE, and you can’t argue with that price.
- [gEDA](http://www.gpleda.org/) (Free and open source, no limitations) – Another excellent FOSS option, gEDA and KiCad are often compared. I tried them both and felt that KiCad was a bit more polished, but you may want to try gEDA for yourself.
- [ExpressPCB](http://www.expresspcb.com/index.htm) (Free, no limitations) – It seems like good software, I have never used it personally but enough people seem to recommend it. ExpressPCB is backed by, you guessed it, ExpressPCB so this makes it very easy to send your design for manufacture.
- [DesignSpark PCB](http://www.designspark.com/eng/page/designspark-pcb-home-page) (Free, no limitations) – I had never head of DesignSpark until I started writing this post. I have to say I am very impressed by what they show on the landing page so I may check it out.
- [DipTrace](http://www.diptrace.com/) (Non-free, prices from $70 – $900) – DipTrace comes highly recommend, I prefer free and open-source software (FOSS) so I have never used it, but it may be worth your time.
- [PCB123](http://www.sunstone.com/pcb123.aspx) (Free, more powerful packages non-free) – This software from Sunstone looks very promising, I’m sure there are some hidden limitations that I couldn’t find, but I will be checking out this package when I start my next design.
- [EasyPC ](http://www.numberone.com/easypc.asp)(Non-free, $500-$2700) – I haven’t used this software personally but it looks well designed (kind of reminds me of Altium Designer), the price is high for hobbyist use but wouldn’t be too bad for a professional.
- [Mentor Graphics PADS](http://www.mentor.com/pcb/pads/overview/) (Non-free, cost unknown, likely &gt;$5000) – This software seems to have fairly poor user feedback, I don’t know why you would choose to voluntarily use it. From what I can tell, most of its current user base is from engineers in a corporate setting that are required to use it for backward compatibility.
- [Altium Designer](http://www.altium.com/en/products/altium-designer/purchasing-options) (Non-free, &gt;$5000) – Altium Designer has excellent user feedback, if you are looking for a professional suite to work with and can handle the price tag, Altium may be your best option.
- [OrCad PCB Designer](http://www.cadence.com/products/orcad/orcad_pcb_designer/pages/default.aspx) (Non-free, &gt;$5000, upgrade path can push you north of $25000) – Cadence OrCad is a behemoth in the EDA industry, unfortunately they also throw that weight around by charging insane prices. If you absolutely need the features offered by OrCad then it may be worth your investment, but for the average user this is overkill.

So I wasn’t lying, it’s a big list! When we narrow it down and look at what’s practical though, I think the first three options are the most interesting for hobbyists.

As I said in the summary, EAGLE is a very popular package and has a huge community of hobbyists that use it for their projects. Unfortunately there are some nagging issues with EAGLE that have caused me to abandon it in search of greener pastures

For various reasons, I ultimately decided on KiCad, but since this isn’t a comparison article I won’t go into details. If you are curious about my reasoning, this article does a good job of highlighting what I didn’t like about EAGLE, though I don’t fully agree with his assessment of KiCad.

*I’m actually using Altium Designer because it’s actually better and <span class="short_text" id="result_box" lang="en"><span class="">widespread</span></span> in professional development.*

Best Practices for Electrical Schematics

As far as I know, there are no standard guidelines for drawing schematics. Most of us learn by trial-and-error, pick up the habits of our teachers, or just never learn. I think it’s time that these guidelines found a home.

The purpose of an electrical schematic is simple, to describe how components are electrically connected. A schematic does not necessarily indicate the physical relationship between components, though a good schematic will make this obvious when necessary.

**The difference between a good schematic and a bad schematic is a matter of how easy it is to understand.** If another person is able to look at the schematic and simply understand it, you have made a *good* schematic, if another person has to look at your schematic and decipher it, you have made a *bad* schematic. Here are my suggestions for making a *good* schematic.

#### Labels and Comments

Labels and comments on your schematic come at no cost to you so you might as well use them. **You should always label your components.** Most (or all?) schematic editors will do this automatically for you, but if yours doesn’t then you **must** do this. There are some generally standard designators in use today, the most common are:

- **R, C, L, and D** – These are the default designators for your most common passive components. R is for resistor, C is for capacitor, L is for inductor, and D is for diode (including LED). These are standard designators and you should not use any other designator for these components. The only exception to diode marking is if you are using a Zener diode, in that case refer to it as Z.
- **M and Q –** Standard designators for transistors. MOSFETs are referred by M while BJTs are referred by Q. M can also stand for Motor, if you are using a motor in your design then refer to all transistors as Q.
- **T or XFMR** – Transformer
- **S or SW** – Switch, this includes pretty much any time of switch, even push-buttons. You can use either designator, but you should only use one. Consistency is key, I recommend SW.
- **X or XTAL** – Generally refers to crystal oscillators, X can also be used to designate subcircuits. I recommend XTAL.
- **U or IC** – Designates an integrated circuit, U is the most common designator but IC is just as clear and well understood.
- **TP** – Test point, these are handy and you should make generous use of test points in your circuit while it is in the prototype stage.
- **JP** – Jumpers
- **J or P** – These designate jacks or plugs, respectively. Jacks are generally female while plugs are generally male.
- **F** – Fuse
- **FD** – Fiducial
- **BT or BAT** – Designates a battery or battery connector
- **X** – Parts not covered by the above rules. You should leave a label near these parts to note their function.

These rules are extremely helpful when sharing your designs with others, or when you need to come back to your design in the future. However, having correctly referenced parts is not necessarily enough to make a good schematic. It is also good practice to **comment on non-standard parts or on important performance details**.

For example, if you have a component that requires a very large power trace or special shielding then you should note this on the schematic. For more advanced circuits, such as RF designs, you would also want to note required trace lengths or impedances.

There are too many examples to list all of the situations in which you should make use of comments, but a good guideline is to **ask yourself “If I were to look at this circuit in one year, would I still know what it is doing and how to take it to layout?”** If it passes this test then you are on your way to creating a successful design.

Another recommendation for making your schematics clear is to be mindful of where your labels and comments are placed. If a label is placed over another label or over a component outline then you might as well not have it there at all because it won’t be readable.**Take the few extra seconds to move your labels into a logical position near the component while not overlapping other components or labels.**

The final guideline for proper labeling is to **remember to label your most important nets**. Don’t go overboard with this, but a few net names to remind you of functionality is an incredibly simple way to ensure that you are making an understandable schematic. Additionally, **keep the names as short as is reasonable, use all caps, and separate words with underscores**.

This means that instead of “Pin going to output” as a label you would want to do something like “TO\_OUT” or even better, just “OUT.” This will ensure that you have readable schematics with signal names that are obvious and intuitive.

#### The Logical Schematic

I’m not certain where the convention came from, but it is always customary that **inputs come from the left**, **outputs go to the right**,**power comes from the top**, and **ground or negative voltages go to the bottom**. I recommend following this convention whenever it is possible and reasonable to do so.

Of course you can’t always do it, but at the very least try to **separate your power pins from your I/O pins**. If you have multiple voltage rails, the more positive voltages are generally higher on the schematic, though this is not a do-or-die rule.

Dot your i’s and cross your t’s. Well, something like that, this is a convention that comes from the days when low resolution photocopying was common. It is universally accepted that you should **make a very clear dot where two wires form an intersection**, your CAD package will usually handle this for you but it is good to keep in mind.

Related to crossing connections, you should also try to **avoid 4-way connection points**. This is another recommendation from the days of photocopying circuits, but it never hurts to design for longevity.

#### Using Hierarchy the Right Way

The final pointer in ensuring that your schematic makes sense is to utilize hierarchy effectively. This means that you **separate logically different parts into a new sheet**. By all means, if you can fit your entire design into a single sheet without cramping it together and still following the other rules, you should do that. Otherwise you might as well separate functionally different parts of the design into separate sheets.

There are different ways to do this in each CAD package, but the basic idea is the same. **By keeping related components near each other and avoiding the clutter of other components you will be able to more easily verify and debug your design**.

If your schematic doesn’t necessarily require multiple sheets then you should still do your best to attempt to introduce a bit of order into the chaos that is an electrical schematic. My preferred method is to draw a box around a functional unit and then place a label inside the box to indicate what that design does.

#### Other Tips

In addition to the general guidelines above, I have managed to compile some other tips that will lead to a successful design. If you have some of your own, feel free to submit them in the comments below (along with an explanation) and I will add them to the list.

- **Show decoupling capacitors near the device they are protecting.** This is one of the few devices where it is important to indicate physical presence of a component. Decoupling capacitors are used to smooth out the ripples at the power supply of a component, in order to effectively do this, they need to be placed physically close to the component. This proximity should be made clear in the schematic.
- **Design for easily printable schematics.** While most schematics today are handled electronically, it is not at all uncommon to want to print the design out, either to share it in a meeting, or to review it with a pen in hand. For these reasons, you should always make sure your schematics are designed to be easily read and analyzed at whatever paper size is common in your area. For the U.S. this is 8.5″ x 11″ for Europe, the most common size is A4 which comes out to about 8.3″x11.7″ or 210mm x 297mm.
- **Make your schematics understandable even if they are printed in black and white.** Many office printers are not capable of printing in color. I also often find that I prefer the look of monochrome schematics when they are printed. If you design your schematic to be readable and understandable without color then it will make it easier to analyze your design later.
- **Air wires.** Use them when you have to, avoid them when it’s practical. The point is to make your schematic as easy to understand as possible, so if it makes sense to put a label on a wire and connect it to others by using that label then feel free to do so. Just keep in mind that air wires can make it difficult to debug your circuit later since you must manually search for all of the connections.
- **Consider revision control.** Undoubtedly, you will end up making several versions of your original design. It is best to plan ahead for this and to manage your different versions intelligently. I like to use a combination of [git](https://www.syntevo.com/smartgit/) with [gitlab](http://gitlab.com) to track my designs, but there are other methods such as manually saving version numbers or date codes into the project name.

Like I said, these are just a few tips I have picked up from my experience, if you have your own then submit them in the comments and I will add them to the article. Now that you know the best practices for getting your design into the computer, get to work! The next step is to start with the physical layout, this is where it starts to get interesting and you will want to have a solid schematic under your belt before you move on.

### Final Preparations for PCB Layout

Now that you have your schematic entered into the computer and all the connections have been validated, you can move on to physical layout of your PCB. This is the most complex part of the design process and there are far too many different possibilities for any single guide to provide a full list of guidelines in a sensible manner. That being said, I will do my best to provide general guidelines for producing a manufacturable and electrically sound PCB.

**If you are interested in the specifics of specialized PCB design techniques, how to use the various CAD tools, and other general workflow improvements** then subscribe to this blog (in sidebar on desktop, below on mobile) to continue receiving articles and guest posts on improving your designs.

#### Choosing a Manufacturer

I’m sure it may seem like a strange suggestion to choose your manufacturer before you begin board layout, but I assure you there is a good reason for this. No two PCB manufacturers are the same and each one has different limitations.

**Definitions:** A “**mil**” refers to a thousandth of an inch. While most engineering processes have standardized on the far more understandable metric system, physical products still rely on imperial units. “**Clearance**” refers to the separation from the edge of one trace to the nearest edge of another.

While one manufacturer may be able to produce 6 [mil](https://en.wikipedia.org/wiki/Thousandth_of_an_inch) traces with 6 mil clearances (3/3) another manufacturer may be limited to a (8/8) setup. **You do not want to design your board and route all of your traces at a very small width only to find that your manufacturer cannot produce the board at that specification.** This could leave you resorting to much more expensive manufacturing options, or receiving a non-working PCB when the manufacturing house attempts to manufacture your design anyways.

If you thought there were a lot of CAD packages to choose from, then you would be truly overwhelmed by the number of different manufacturers and assembly houses there are. Rather than compiling a huge list of all of the PCB manufacturers and assemblers, I am just going to post a short list of those that I either have personal experience with or that have made a strong impression on me.

- [OSH Park](http://oshpark.com/) (Low cost fabrication, U.S. based company) – If you just need to do a small order of PCBs, don’t need assembly, and your design fits within their limitations, I fully recommend OSH Park. The turnaround time isn’t stellar, but in the 2 weeks you may end up waiting for a board, you can always start working on other projects.
- [Advanced Circuits](http://www.4pcb.com/) (Incredible flexibility and turnaround time, also offer assembly, U.S. based operations) – I have never used their services personally but I have to say I am impressed with what they offer and others seem to be happy with their results. Their prices for short run fabrication are much higher than OSH Park, but their medium run prices (50+ boards) are perfectly reasonable and they offer a wide range of fabrication options. They also offer a “Barebones” option that is excellent for prototyping.
- [Gold Phoenix](http://www.goldphoenixpcb.com/) (Cheap higher quantity orders, non U.S. based) – I have also never used Gold Phoenix but they are apparently often used by SparkFun and offer good prices on larger orders. Their services are based out of China and their boards are not as high of quality as Advanced Circuits, but they are worth a shot for medium run production.
- [ExpressPCB ](http://www.expresspcb.com/)(Software integrated solution, reasonable pricing) – ExpressPCB is the only one on this list that also showed up on the CAD list as well. From what I can tell, their quality seems to be about on par with Gold Phoenix with a similar pricing structure to Advanced Circuits.
- [Seeed Studio](http://www.seeedstudio.com/depot/services-c-70_71/) (Reasonable pricing, not as many options as Advanced Circuits, but more freedom than OSH Park) – Seeed studio has made a point to focus on hobbyist work and their dedication is clear. You can get a 2-layer 5cm x 5cm board starting at $9.99, and they include free testing which is a great deal.
- [SFCircuits](http://www.sfcircuits.com/) (Not as low budget as others, better suited for large or complex boards, including assembly) – I’ve also never used their services personally but have heard good things. They offer a couple U.S. made hobbyist specials but it’s not their core service. They are a good place to start for larger production runs and more complex layouts.

*You also can find other services in China which can be more suitable sometimes.*

These are just some of my recommendations, but as I noted earlier, there are many, many more out there. Suggest your own favorites in the comments below.

#### Defining your Design Rules

After choosing a manufacturer you should make note of their manufacturing constraints. As an example, at the time of writing the minimum specifications for OSH Park were:

- 6 mil copper traces
- 6 mil spacing between traces
- 13 mil drill diameter
- 7 mil annular rings \[Defined as (diameter of the pad – diameter of the hole) / 2\]

This means that these should be the smallest features you use under any circumstances. **Using smaller features will likely result in broken traces, overlap of traces and copper fills, or busted vias.**

Once you determine these rules, you should head into your CAD software and define them. This will enable some design for manufacture (DFM) checks to take place as you design so your program will not allow you to perform operations that will cause you to have non-manufacturable boards.

This is one step of the process where EAGLE generally has a distinct advantage over KiCad, most board houses provide a design rules file that can be imported directly into EAGLE. This saves a few steps in defining design rules, and reduces the chances that you will end up with incorrectly defined rules.

**Note:** Just because your fabrication house can do a 6 mil trace doesn’t mean you should use exclusively 6 mil traces. You should use the largest traces possible that will still allow you to fit your design in the required space. Using larger traces improves reliability, decreases parasitic resistance, and as a whole results in a better circuit.

#### Do I Need a Ground Plane?

One of the more debatable topics in designing a PCB is deciding **whether to include a ground plane or not**. While it is nearly standard practice to include a ground plane in your design, this is not always required and can in some cases actually result in worse performance. But how can you know when you should and when you shouldn’t?

First, it helps to know what a ground plane is. Simply put, **a ground plane is a copper layer on your PCB that acts as a common ground to many devices**. It is called a ground plane because it often occupies an entire layer, which creates a planar surface to conduct charge.

**What are the benefits of a ground plane?** There are several benefits to using a ground plane in your design, the most common are to provide electromagnetic shielding, lower the resistance of the path to ground, and to assist with heat dissipation across the board. These benefits are excellent for the vast majority of designs, but there are also some drawbacks to using a ground plane in your design.

**What are the drawbacks of a ground plane?** Perhaps the largest drawback of using a ground plane is the increase in parasitic capacitance. Parasitic capacitance is an undesirable effect that will essentially cause your circuit to be less “responsive” than intended. For most applications this is just fine, but for exceptionally quick response circuits it may be worth removing the ground plane.

Ultimately, it is up to you to decide whether you need a ground plane or not. Here are a few guidelines to help you make the decision:

- If your design is not particularly high performance, **it’s your call.**
- If your design includes RF range signals, you should **always use a ground plane.**
- If you have components that rely on fast changing input signals you may choose to **not use a ground plane at all** or to**remove part of the ground plane around those inputs**.
- If you’re just not sure, **use a ground plane**. The chances are in your favor that the circuit will behave as expected with a ground plane, even if that is not required. The opposite is not quite true.

#### Special Considerations

In addition to considering the ground plane and adhering to design rules there are some other special cases in which you may need to consider other effects.

- **Designing for RF** – If your design will be operating in the radio frequency range or using similar high frequency components, there are many special design factors to consider. This topic is too in depth to cover right here, right now, but this post from EEWeb outlines some good notes to get you started.
- **Mixed-signal designs** – If your PCB carries both analog and digital signals then you will want to make certain that you have fully separated these signal paths. The fast changing voltages used in digital circuitry can cause your analog circuitry to behave erratically. Mixed-signal design is a whole field of study on its own (as-is RF) so if you are working with these designs it may be best to seek the help of an experienced designer.
- **High voltage work** – High voltage circuits require extra care when designing and testing so as to avoid exciting outcomes like heart-stopping electrocutions, electrical fire starting mishaps, or other disasters. If you are designing for high voltage applications then stop reading and seek the assistance of a grizzled old electrical engineer experienced in high-voltage designs.

Once you’re absolutely certain that you should be capable of designing the circuit yourself, you can move on to the next step.

### Get to Work!

Finally, what we’ve been working towards the whole time. Now that you are a few hours (or days, or weeks) into the design process, you can finally start working on what you have been planning so carefully for. But you do have one more decision to make first…

#### **To Autoroute or Not?**

Should you use the wonderful autorouting features of your CAD package or not? For those who don’t know what an autorouter does, it automatically connects the traces in your board in a pattern that the software deems is most efficient. Some CAD packages also include an “Autoplacer” which will automatically place your components for you before routing.

**In general you are probably better off avoiding both of these tools** for simple hobby work or even moderately complex designs. Honestly, if you have a thorough understanding of your circuit, and you should by now, then you will be able to do a better job of placing and routing components.

There are of course a few exceptions to this guideline. If the design you are working on is complex and it would take you weeks or months to perform a proper layout by hand, then you should try to get access to an advanced CAD package to make use of the significant research these companies have put in to autorouting algorithms.

In addition, if you are just dreading the idea of sitting at a computer ensuring that your design is perfect, then you may just wish to place your necessary components, lock them into place, route the critical connections, and then run the autorouter. **This is the recommended way to use the autorouter if you choose to do so.**

#### Drawing the Board Outline

The first step is to draw the outline of your board. This layer tells your fab house where to cut to give you the right sized PCB.

To draw the board edge you will begin by switching to the layer that is designated for cutouts. Depending on your CAD package, this could be “Edges”, “Board”, “Cutout”, or something else along those lines.

After selecting the board edge layer make good use of your drawing grid to ensure that you have straight lines of a well-defined length. If your board needs to be a specific size then make sure you are using the correct measurement units for your grid. If you draw your board in mm instead of inches, you will get a little surprise when you try to place your parts and can’t fit them all on the board.

A few tips for drawing your board edges:

1. **Set your drawing grid at a reasonable spacing** and make sure your cursor is set to **snap to the grid.**
2. If you are using EAGLE or another program that supports it, **make use of the keyboard commands for defining lengths of segments**.
3. **Consider using alternate axes** (plural of axis). Most CAD software supports some method of setting an alternative origin point, this will allow you to draw lines of specific length without needing to subtract coordinates in your head. If your CAD package supports #2 then you may not need to use this feature, but I have found it helpful in KiCad.
4. **Ensure that all the edges line up exactly**. If you have a spot on the board where two edges meet but don’t quite touch, then you should fix that now. Trying to send your board to the fab house like this will result in them responding to you with a solid “No thanks.” Fix this issue before it becomes a headache to fix.

**Alternative Method:** If your board doesn’t need to be any specific size or shape then you may want to wait until the end to draw your board edge. But if you have any predetermined requirements for the board, you will want to start with this step.

#### Placing Components

Next up, you will want to place all of your components inside the board outline. **You should start with components that have a set physical location** such as connectors or sensors that can’t be blocked.

After that, you will want to **begin placing your ICs.** **Start with the largest ICs first and then place the smaller ICs as you go**. ICs with more pins will require more room around them for routing traces and placing auxiliary components. **Try to leave extra room around devices that have many pins.**

Another thing to consider when placing devices is to **try to keep all your ICs oriented in the same direction on the board.** This is not a strict rule, but it can sure make assembly much simpler and is generally not a bad rule to follow. If it just isn’t possible then don’t worry about it.

**Once all of your physical components and your ICs are in place you can place the supporting devices.** Things like resistors, capacitors, diodes, etc. This is a good time to refer back to your design notes and make sure that any components which need to be physically close to an IC are in a good position. If you have components that have these requirements then I would recommend locking them in position after placement.

One final thing, you will want to consider **leaving space for annotations and markings on the board**. I’ll discuss these things in more detail in a bit, but you’ll want to make sure there is enough space around your components to leave some lettering near anything that may need it. For more info on this, jump down to the “Adding Some Style” section.

#### Making Connections

So, everything is in position and the board is starting to look like it will come together. The next step is to make it all work! You could just start by connecting pins all willy-nilly as you see fit, but taking some time to do it right will pay off in the end, which is coming sooner than you think.

There are two recommended ways of starting out laying your traces. You can begin by routing your power traces first and then focus on everything else, or if your design has high frequency signals you can begin by routing those first. Other than that, the rest of the connections are up to you.

While there isn’t any single “right” way to lay-out the rest of your PCB traces, there are some methods that are “more right” than others. You can see my recommendations below, and I hope to see a few more additions come from the community.

1. **Make use of thick power supply traces.** The power supply rail will most likely be the most active trace on your PCB and since it will be supplying the more current than any other trace it also deserves some special attention when determining how wide it should be. As a general guide I like to use 20 mil power traces. For low power circuits this is probably overkill and you could get away with less, for higher power circuits this may not always be enough. If you are designing circuitry that is going to draw current in the Ampère range as opposed to milliAmpère then I suggest taking a closer look at your trace width. [This handy calculator](http://circuitcalculator.com/wordpress/?p=25/) will help you calculate the correct width to use for your traces.
2. **Avoid routing two (or more) high frequency signal traces in parallel with each other.** According to Ampère’s law (with Maxwell’s correction) we know that a changing current induces a magnetic field around the wire, we also know that a changing magnetic field induces a current perpendicular to the direction of the magnetic field. This effect can cause two parallel wires to couple together so that a change on one wire can induce a change on the other. You can avoid this by keeping high frequency traces separate and only crossing them in perpendicular alignment.
3. **Try to group similar signals together.** If you have a bunch of wires coming from a single device that all perform a similar function then you should try to keep them neatly grouped until it is absolutely necessary to split them up. This will allow you to more easily follow the signal path and will help you end up with a cleaner looking board after fabrication.
4. **Minimize your use of vias**, but not at the cost of dramatically increasing signal paths. This recommendation may just come as a result of my fascination with aesthetic design, but there is also a practical reason to use fewer vias. The simple point is that vias are a manufacturing risk. While it isn’t likely that your board house will mess up and drill a hole too large or break the conduction ring, it is completely possible. Having fewer vias on the board reduces this risk. Another benefit of reducing vias is that it results in a shorter signal path (even if only a tiny reduction). This type of caveat is really only important in RF designs, but if there is a way to improve a circuit, I’m always looking for it.
5. On the other hand you could, **use two inline vias at every signal pin.** I know this may make me look like a hypocrite or an otherwise very confused person but there are also situations in which more vias could help. If you are working on a prototype circuit, extra vias allow you to easily create test points, and to simply cut and reconfigure traces. This recommendation comes courtesy of a reader, James Edwards I believe, but I couldn’t find the original comment.

There are probably some more useful pointers that I’m just not thinking of, but nothing comes to mind right now. I will add more as I think of them.

#### Adding Some Style

You’re almost there, the last major step before moving on to manufacture is to add the finishing touches to the board. This may seem like it’s just aesthetics, but there are several practical reasons to include some extra markings on your board.

The first decision you need to make is whether or not you should include component reference numbers or values. As an example, do you want your final design to indicate that “this” resistor is R11 and has a value of 4.7k or do you want to just mark it as R11? Maybe you don’t want to mark it at all?

This is really up to you. My thought is that you will be one of the few people who actually looks at the board components and if you are looking at the board you will be able to easily pull up a schematic for reference. For that reason, **I do not include reference numbers or component values on my final designs.**

Having said that, there are some components that can benefit from a bit of labeling. **Generally you will want to label any LEDs, buttons, switches, connectors, or otherwise important devices.** I guess the argument could be made that ALL the components are important, but I am specifically referring to parts that would be good to know when using the device.

#### Final Design Checklist

The design checklist is included as an appendix in the downloadable print-ready version of this guide linked below.

#### Manufacturing The Board

Since you should have chosen a manufacturer by now, this part of the process is going to be relatively easy.

The first step in preparing your design for manufacture is of course to perform the final design checklist. Since we covered that in the last section, it’s okay to go ahead with the rest of the manufacturing process.

#### Run a Design Rules Check

Before going any further, you will want to run one final DRC. This generally checks that your PCB layout matches the schematic and that your layout follows all of the design rules that you defined. If the DRC catches errors, you should review each one individually and either fix the problem or mark it as a false warning.

Another thing to check is that all of your connection shave been made. Sometimes the DRC tool does not check connections, or your ratsnest may be too small to notice. You want to be extra certain that all of the board connections are complete before moving on.

#### Generate the Bill-of-Materials (BOM)

A bill-of-materials (BOM) is used by the assembly house, or for your own use. Either way, it is important to have a good list of your parts. Here are the important details to include in a BOM:

- Component reference designator
- Component package
- Quantity required for one PCB
- Description
- Manufacturer
- Manufacturer reference number
- Supplier
- Supplier reference number
- Cost per unit
- Alternative parts allowed, if applicable
- Comments

Most CAD software can export a BOM automatically, but you will generally want to format it and make sure that everything is correct.

One reason to make a good BOM, even if you are not using assembly services, is because many parts suppliers will allow you to upload this file directly to their website and automatically purchase components. I know Mouser and Digi-Key support this, others may as well. **This method will save you hours of time searching for components and adding them to your order.**

#### Export the Board Files

Each fabrication house will have different requirements for how you should submit your design but nearly all of them accept one common file format called “Gerbers.” Some will even accept your CAD files directly, but this isn’t universal and you shouldn’t rely on it.

Each software has a different process to follow in order to get Gerber files out, here are some tutorials that show you how to export Gerber files from EAGLE, KiCad, Altium.

- [Prepare EAGLE files for manufacture](http://hackaday.com/2009/01/15/how-to-prepare-your-eagle-designs-for-manufacture/) from Hack-a-Day
- [KiCad Tutorial: Gerber file generation](http://www.wayneandlayne.com/blog/2013/02/27/kicad-tutorial-gerber-file-generation/) from Wayne &amp; Layne
- [How to generate Gerber files in Altium Designer](http://support.seeedstudio.com/knowledgebase/articles/1118680-how-to-generate-gerber-files-in-altium-designer)

#### Final Manufacturing Checklist

The manufacturing checklist is included as an appendix in the downloadable print ready version of this guide linked below.

#### Send it to Your Manufacturer

That’s it! Depending on the service you chose for manufacturing, the instructions will vary, but from here on out the process is relatively straightforward. Upload your files, cross your fingers, and hit submit.

### The End

That brings us to the conclusion of this series, I know you’ve been hit with a lot of information. If you read both part 1 and part 2 in their entirety then you soaked up over 11,000 words of PCB designing goodies. That’s more information than a silverback gorilla retains in its whole life\*!

\*Maybe, I have no data to back this up.

I hope you’ve found at least parts of this guide to be helpful and that you will make use of it in your future designs. I attempted to make it general enough to be useful for any CAD package at any point in time. When searching how to do stuff like this it is incredibly easy to stumble across information that just isn’t relevant anymore, so I hope this will help.

I worked on this post off-and-on for about two weeks, even though I reviewed it several times before posting, **I don’t make any claim that it’s perfect.** If you see issues in my writing or think my advice is bad then feel free to let me know.

If you like the content of this post then I hope you’ll **consider subscribing**, or at least checking back regularly. I have some interesting articles coming down the line such as:

- Quick guides for making add-on boards for the most popular prototyping systems.
- In depth tutorial on using KiCad to design PCBs.
- Product reviews of some common tools of the electronics hobbyist.
- And much, much more 🙂

*Materials for this article was copied from [here](https://www.pcbway.com/project/share/How_To_Design_the_Perfect_PCB___Part_1.html) with some additions and changes*
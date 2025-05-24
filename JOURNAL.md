---
title: "T430 Ultrabay Companion Core"
author: "Fionn (WheeledCord)"
description: "A Raspberry Pi based co-processor module that fits inside the ThinkPad T430 (And hopefully similar models) Ultrabay."
created_at: "2025-05-22"
---

## 23/05/25
### A little backstory:

I recently purchased a ThinkPad T430 for 60 dollars ($35 in freedom coins). It's pretty nice, though it's missing a battery and an optical drive. I ordered a new battery, but who even uses the optical drive nowadays? So, left with this empty space on the side of my laptop, I of course started thinking about what I could put there. Initially, I considered building a WiFi adapter module with an external antenna. Sure, it would look sick, but realistically, I can just plug one in via USB. That brought me down to two main ideas:

- An SDR module (Software Defined Radio)
- A Raspberry Pi co-processor module

I ended up going with the latter, mainly because SDRs are expensive :(

### Research
Here are my core design goals:
- Thin enough to fit inside the ~12mm tall Serial Ultrabay Enhanced.
- Powered by the 5V SATA power line
- Ideally boots without human input

My first thought was the Raspberry Pi Zero 2 W. It's very small, should be powerful enough, and can be powered by the 5V I get from the SATA port. Though I think it may be too small. Although its height is perfect for my usage, I feel like I could use something more powerful that doesn’t leave a lot of wasted space. That leads me to my next idea: the Raspberry Pi 3 A+.
I couldn’t find an exact measurement of its height anywhere, but it seems to be around 12 mm. That would barely fit, and since I want a case, I need to factor that in as well. I could definitely make it much thinner by trimming down the headers—and maybe even the ports.
Another option I found is the Raspberry Pi Compute Module 3+ with a custom carrier board. Perfect in theory, right? A custom carrier board would mean total control over the size, shape, IO, etc. The problem is, I have zero prior experience with PCB design.
Before deciding on which board to use, I sketched out a rough template of the size and shape of the case that will go in the Ultrabay, based on the standard Serial Ultrabay Enhanced optical drive.

<img src="https://github.com/user-attachments/assets/9df797d9-3733-4b6c-aa58-ce4df23fb898" width="400"/>

It looks a little funny, because I drew it out based on reference images, without getting the measurements first (and I didn't have a ruler, so I used a Steam gift card), but this should be good for making a 3d model for it. I'll probably hollow it out and get my friend to 3d print it, so I can get a feel for it. 

<img src="https://github.com/user-attachments/assets/53f3d6d3-d7ec-42be-a7cd-015ad86d6c5a" width="400"/>

A few hours later and I have made the 3d model for the container. I hollowed it out to save filament, and so I can see how much it can store in person. The main hole goes 11 mm deep, so I hope that will be enough to fit everything I need. As of writing this, I have just sent the email to my friend, and will probably go to sleep now, as it is past midnight. Or I might watch a few videos on PCB design. Still need to learn that.

## 23/05/25
### PCB design time

I know next to nothing about PCB design, but for the Co-processor, I think I'm going to use the Raspberry Pi Compute Module 3+, meaning I have to design a carrier board for it. If that ends up being too hard, I'll probably use the Raspberry Pi 3 A+, and if that somehow fails, I'll use the Raspberry Pi Zero 2 W.

After some research, here are the things I'll need:

- Compute Module 3+ socket (SODIMM-200)
- Power Input (from SATA power)
- USB OTG interface (Gadget mode)
- EEPROM
- 28x132 OLED I²C Display
- GPIO Breakout

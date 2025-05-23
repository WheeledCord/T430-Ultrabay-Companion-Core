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

My first though was the Raspberry Pi Zero 2 W. It's very small, it should be powerful enough, and should be able to be powered by the 5V i get from the sata. Though I think it may be *too* small. Although it's height is perfect for my usage, I think I could get something more powerful, and doesnt leave lots of wasted space, which leads me onto my next idea; The Raspberry Pi 3 A+. Though I couldn't find an exact measurement of the height anywhere, it seems to be around 12mm. That seems like it would barely fit, but considering the fact i want a case, it should factor in that as well. I could definitely make it much thinner if i were to trim down the headers, and maybe the ports as well. The other option I found was Raspberry Pi Compute Module 3+ Lite, with a custom carrier board. Perfect in theory, right? Custom carrier board = total control over size, shape, IO, etc. The problem is that I have *zero* prior experience with PCB design. 

Before I decide on what board to use, I sketched out a template of the size/shape of the case which will go in the ultrabay, based off the regular Serial Ultrabay Enhanced optical drive. 
![IMG_3481](https://github.com/user-attachments/assets/9df797d9-3733-4b6c-aa58-ce4df23fb898)
It looks a little funny, because I drew it out based on reference images, without getting the mesurements first, but this should be good for when I make a 3d model for it. I'll probably hollow it out and get my friend to 3d print it, so I can get a feel for it. 

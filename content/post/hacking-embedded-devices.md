---
author: "Simon Tulling"
title: "Hacking the Cassida Zeus"
date: 2023-06-29
description: "Guide to hacking embedded devices without desoldering"
tags: 
- hacking
---

> Note: The actions in this post have taken place somewhere in 2022 and a step in the process leveraged an oversight in the _Cassida Pro_ website which has since been fixed.

## Introduction
This post will walk through the steps in hacking an embedded machine from A to Z, with any and all pitfalls that crossed my path. If you think I made a mistake or could've taken an easier route, please let me know and I will add it to the post.

[^1]: ...or lack thereof

## Background
As a supervisor at [Makerspace Delft](https://www.makerspacedelft.nl/), I often got my hands on some high end trash. It's located on the south side of Delft in an abandoned cable factory[^2] which has been repurposed for hobbyists and startups, although they want to [revamp the entire place in the near future and turn it into a mixed purpose district](https://kabeldistrict.nl/) which makes the future for these kinds of businesses uncertain. Anyhow, I will agree that the place is in need of a cleanup but its shadyness probably led into the creation of this post.

Anyone who's been to the Netherlands knows that cash is rarely used nowadays, except by the elderly and drug dealers. While I don't want to point fingers at who this money counting machine may have belonged to, the fact that it was found closely following a drug bust in a run down factory may give some slight hints. I'll leave the connecting of the dots as an exercise to the reader. 

[^2]: ![Kabelfabriek](cassida/kabelfabriek.PNG)

### Why hack into it?

So near the back of the building in a dumpster we found this [Cassida Zeus](https://cassidapro.com/solutions/zeus/) machine. A cursory google search gave us some hints that we were dealing with a money counter / verifier.

When plugging it in, it looked good to go, the screen lit up and everything. Between the 3 of us that took it out of the machine we had a single cash bill[^3] and put it in. After the motors almost tore the bill apart without counting we didn't know what to do with it. Fixing it is an option, but unless one of us had aspirations in dealing either cards or drugs that wasn't too useful.

I opted to take the machine and try to hack into it, it was my first time trying something like this but seemed like a fun challenge.

[^3]: Which shows the usefulness of such a machine here

## Examining the machine
![Cassida Zeus](cassida/zeus.PNG)
**So yeah, where do we even start?**  
What I did at first was look around the machine and see what capabilities it had.

![Cassida Zeus Backside](cassida/backside.PNG)

Based on this image we can see:
- USB type-a connectivity. Perhaps for a usb stick to update firmware
- USB type-b connectivity. Possibly a serial port to talk to the device
- Ethernet Port. So at least the machine can connect to the internet
- External Display Connection Port??
- Thermal Printer Connection Port??[^4]

[^4]: Remember that note at the start with the updated website? They aparently also updated the documentation. The documentation I had used didn't explain the use of the connection port, so I just assumed it was a serial port and wasted time trying to communicate through it. 
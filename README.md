# Recovering data from a bricked Raspberry Pi CM4

## The Problem
I like the CM4, but it's pretty easy to blow them up. The PMIC doesn't have any kind of short overcurrent protection, so if you short any rail to ground, or any pin driven high, it will die. Replacement PMIC's are *almost* available, but not quite. Earlier versions of the chip are on sale from Mouser, etc., but not the P4 revision that's on the Pi 4 / CM4. That may have changed by the time you're reading this. In any case, replacing the PMIC won't help if your SoC is also dead.

I've blown up three of them so far by doing various stupid things. They're not expensive, but if you've got some critical data stored on one and it ain't backed up properly - expect trouble.

To avoid cross-compilation I had been doing quite a lot of work on the Pi itself, working on a custom kernel module. I hadn't noticed, but quite a few vital files weren't checked into git, and I'd been a bit sloppy with regular pushes anyway, so when I accidentally dropped a scope probe on the 

## The Solution
Luckily, eMMC chips are electrically compatible with [micro]SD cards, so all we need to do is convert the dead CM4 into an SD card. What follows is a description of how I figured out how to do it, and a guide for you to follow if you find yourself in a similar situation.



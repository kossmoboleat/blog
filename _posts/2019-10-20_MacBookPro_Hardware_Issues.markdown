---
layout: post
title: MacBookPro Hardware Issues
date: 2019-10-20 09:00
---

## two replacements in one year = new laptop

Over this year I've had numerous issues with my work laptop. One after another its graphics chip and keyboard have failed. I'm using a late 2016 MacBook Pro 15-inch laptop with Touchbar. Overall the machine is a fine piece of hardware although I don't really see the point of the Touchbar and would prefer regular ports instead of 4 USB-C ports.

The keyboard problems are well known. It's rumored that there will be newer 16-inch models coming out soon, that use a different kind of keyboard switch again to fix the problem for good. At least Apple repairs the keyboards free of charge, when they start to fail. That's what happened to my laptop and they had to replace the battery too, because they're soldered together. There was some issue with my display too and the friendly service worker told that there's another offer for free replacements open for that :-). After both repairs every part of the laptop has been replaced except the bottom case.

## mysterious performance problems

My earlier hardware problem was actually quite hard to detect and even harder to analyze. I only noticed something was wrong because my computer became soo slow in hangouts video calls. The connection became extremely choppy. I hesitated to attribute it to a hardware error. Even after improving the air circulation the issue remained. The problem curiously went away when I unplugged all devices from the laptop. This turned out to be a good indication, but I was still not 100% sure it wasn't some other root cause.

## slow as a 800MHz snail

After a lot of desperate googling I found that users in comparable situations figured out what their laptop was doing using the "Intel Power Gadget" (IPG). It not only measures utilization, but also tells you how hot the CPU is and crucially at which frequency it's currently running. I could clearly see now that not only was my CPU highly utilized, which other colleagues experienced too at a lesser degree. Additionally, I saw that the CPU's frequency was quite low at 800MHz instead of around 2.8GHz as expected.

Turns out modern Intel CPUs have a "standard" frequence that they usually run at and a max burst frequency they can only sustain for brief periods. Usually the burst frequency cannot be sustained when more than one core is busy. However the computer doesn't make a binary decision between these two frequencies. It's constantly evaluating load and temperature to choose the best current frequency. Values aren't clear cut nice 100MHz increments but IPG only makes it seem so. When the computer is under a lot of stress it even throttles down the CPU to lower than base frequencies. This is what happened on my computer, whenever an external display was connected and there was high CPU usage.

On the [MacRumors forum](https://forums.macrumors.com/threads/automated-tool-to-reveal-throttling-and-overheating-github.1731178/) someone even created a tool "macoh" that starts a CPU stress test, measures the utilization, frequency and temperatures. Using the resulting graphs it was pretty easy to see that whenever the dedicated graphics card was active the laptop worked much worse than what others seeing.

The MacBooks are not very forgiving thermally. It seems that Apple made them really thin but sacrificed maximum performance in doing so. The heat cannot be efficiently shed. That was the main issue with the newer MacBook Pro's late last year. Where newer processors where slower in some video encoding benchmarks because they just overheated too much. Apparently, Apple has done something to reduce the issue, but I assume it's an inherent design flaw.

## Conclusion

With more research I discovered macs automatically activate the dedicated graphics card when you connect a display. The technicians finally diagnosed that my computer's dedicated graphics card was faulty and had to be replaced. I cannot be 100% sure that this is the reason, because many parts had to be replaced at the same time then. In the MacBooks mainboard, CPU, RAM and SSD are soldered together.


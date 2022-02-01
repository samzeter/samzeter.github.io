---
layout: post
title: Kay Tremolo
---

# Files
[![Order from OSH Park](https://oshpark.com/packs/media/images/badge-5f4e3bf4bf68f72ff88bd92e0089e9cf.png)](https://oshpark.com/shared_projects/oZEiB13o)

[Schematics and PCB](https://github.com/samzeter/kay-tremolo-guitar-pedal)

# Notes
This was my first fully finished guitar pedal, so it's rough but ready.
 
I am indebted to General Guitar Gadgets for the schematic.

The circuit itself is simple, where a Twin-T oscillator circuit is fed into the output. Ideally, redesigning this circuit, I'd add input and output resistors to ground to prevent popping.

Things to consider when building this circuit:

- The two 100K resistors influence the stompbox's output. Initially, I had issues with significant signal loss when the pedal was engaged. Lowering these values to allow more signal through fixed the problem.
- Use transistor sockets to play around with suitable outputs. From readings online, the hfe levels of the original boxes were between 100-150. A common problem people had was using too higher gains and producing, basically, a distortion box. I used my transistor tester before soldering to ensure that this would not happen; however, it would have been interesting to try other transistors. (I used 2N2008s).
- Likewise, you could add sockets for the two 100K resistors if you are not going to breadboard the circuit before soldering, as these will most likely have to be modified to taste.

# Photos
![]({{site.baseurl}}/assets/images/kay1.jpg){:height="500px" width="500px"}
![]({{site.baseurl}}/assets/images/kay2.jpg){:height="500px" width="500px"}
![]({{site.baseurl}}/assets/images/kay3.png){:height="500px" width="500px"}
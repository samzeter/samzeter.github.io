---
layout: post
title: MFOS Noise Toaster
---

# Files
[kicad files](https://github.com/samzeter/noise-toaster)

# Notes

At the time I started this project Ray Wilson had passed away and there were no Noise Toaster PCBs to be found online.

I did the design as shown in Make: Analog Synthesisers in Altium but I changed this to use Kicad, as I wanted to learn it (it's great) and I hate overpriced software.

I used PCBWay to manufacture the board, which means it's a fraction of the cost of buying one from a few different retailers.

An issue with the design is that transistor Q5 found in the white noise generator needs to be experimented with so that the breakdown voltage is met.

The only nasty part of the design I did was to ground the metallic standoff holes on the PCB's ground plane. This caused an error when I assembled the components to the metallic backplate, as I was unintentionally grounding more than I should have. The board schematic / PCB layout should be updated so that the standoff holes are tied to virtual ground instead (BN).

Also you should be careful what libraries you use with Kicad. I used some of Digikey's library parts, and the pinout for some of the transistors was not at all correct. Thankfully I found this issue before fabrication.

Final Gerbers/Archive.zip is what I sent off for fabrication.

**As noted, I'd change pad grounding and also make pin sizes (for X1 through to X27) larger for AWG 22 wires.**

# Photos
![]({{site.baseurl}}/assets/images/noiset1.jpg){:height="500px" width="500px"}
![]({{site.baseurl}}/assets/images/noiset2.jpg){:height="500px" width="500px"}

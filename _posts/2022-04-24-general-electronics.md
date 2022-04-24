---
layout: post
title: General Electronics Notes
---

Some notes on electronics stuff I can't seem to remember grok.

# Components
## Wires

- 24 AWG is best. RG / DIYStompBoxes recommends. https://www.jaycar.com.au/6-core-alarm-cable-sold-per-metre/p/WB1598
- 22 AWG will be a good thicker/ stronger wire
- Solid core can be good for very small patches.

##  Shielded Wire
RG174 is best type for shielded wire. (RG on DIYSB)
Good for high gain pedals, especially if there are high impedance connections to
switches and controls, even if the outer enclosure is metal.

## Capacitors

### Electrolytics
We use electrolytic capacitors because until recently there was no way to make caps in the half-to-one microfarad and up range small and cheaply enough to do the job.

Make no mistake - electro caps are a second choice if you can get nearly equal value for capacitance, small enough volume, and cheap enough to buy. But until recently, alternatives did not exist. So electros were not second choice, they were the only choice.

Those boundaries have been pushed back only by modern manufacturing and materials.

### General Guidelines
For guitar pedals and "through hole" components (ie. not surface mount) you will go a long way without any trouble sticking to this simple set of rules:

less than 1nF:  use Ceramic caps  (preferably NPO or equivalent and not too big)
1nF to 100nF:  use film caps
Non polarized  larger than 100nF and smaller than 10uF:
               For good quality and reliability use film caps but for small size use non-polarized electrolytics.
               Larger film caps can get very large!
Non polarized  larger than 10uF use non-polarized electrolytic
Polarized caps: Use electrolytic caps

### Carson's Guidelines

NP0/Mica - RF capacitors/oscillators (very stable)

X5R/X7R Ceramics - Good RF bypass, Not for oscillators

Tantalum - Not good for audio (nonlinear) good for stability eg 555 timer

Polypropylene - Good for audio

Best Brands:

Through Hole

Metalized Polyester Film Capacitor: Panasonic ECQE(F) - 0.001uF -> 10uF

Metalized Polypropylene Film Cap: Panasonic ECWF(A) - 0.1uF -> 6.8uF

SMT

Stacked Metalized Plastic Film Chip Capacitor Panasonic ECPU(A) 0.1uF - 1uF (16V)


# Impedance


Input Impedance: 
_A measure of the opposition to current._
_The amount of resistance to an AC signal._
_Resistance that varies with frequency._

[Good explanation is found here](http://www.muzique.com/lab/imp.htm)

TLDR; Keep the impedance high to preserve the voltage level drop due to voltage divider effect.

The instrument will have an (serial) impedance which connects to the input
impedance of the device. The input impedance of the device is connected to
ground, hence a voltage divider between instrument output and device input is formed.

So the voltage to the instrument is found using the V Divider rule:
- Vout = Vin * ( Input_Resistance-Impedance / Ouput_Resistance + Input_Resistance)

![]({{site.baseurl}}/assets/images/impedance.jpg){:height="500px" width="500px"}

_Example_
If Vin = 1 and Ouput Impedance of the cable+guitar is 15k and the pedal input is 100k then:
Vout = 100k/(115k) = 0.86 Volts ... which is quite a loss of voltage.

However, if input impedance is very high we keep a lot of our voltage, for instance, 1M:
Vout = 1M/(1+15k) = 0.98V

In general, the ideal situation is to have a low output impedance connected to a high input impedance in order to pass the best fidelity signal across the audio frequency band.

** Passive Filters
TLDR; voltage divider of R+C combo's cause frequency losses.

*** Low Pass

----R------- Vout
       C
       |
       |
       |
       GND


This is a voltage divider. Where Vout = (Xc / Xc+R) * Vin
Using Reactance = Xc = 1 / wC, it can be seen that upon substituion,
Vout = Vin / wRC.
when frequencies get higher, the reactance and output gets smaller. Less reactance = more impedance.

*** High pass

----C-----V_out
      |
      R
      |
      |
      GND

Another voltage divider. However Here Output is defined as

Vout = Vin * (R / Xc + r) .... after substituion:
Vout = Vin * wRC / (wRC + 1) ; When w / frequency is small, v out is small.




# Amplifiers
## Premamplifiers

### Input stage
A record player produces PHONO output which needs to be converted to a LINE LEVEL/AUX signal.

*Expected signals strengths*

- Aux-Level: -10 dBV (0.300 Volt) (DVD players, tape recorders).
- Mic level: -60dBV to -40dbV (0.001 - 0.010 Volts)
- Phono Level: 2.5mV
- Line level: 0dBV (1.0 V)  (or 1000 greater than mic level). (Mixers, audio equipment)


## Stages of a Guitar Pedal
### Input Stage

The audio input is in the range of __ and is coming from a guitar most likely.

#### Input Capacitor

An input capacitor is almost always put in series with the incoming signal. This
blocks DC, removes hum (is a high pass filter). Electrolystics are a poor choice
as their capacitance is directly related to their working voltage. Best/always
use polypropylene, or metallized polypropylene capacitors.

The input impedance of a guitar can be measured, then it's Z value incorporated
into the low-pass filter equation to determine the amount of roll off the
capacitor will provide.

The equation:
1/(2pi*Z*C)

Decoupling capacitors can be used. These lead to ground and reduce noise.


# Testing

## In circuit testing
There is really only one method to check a transistor in-circuit and here it is.Short the base-emitter junction and observe the collector voltage rises on a good transistor. Clip one half the base resistor value (or 1K) from the positive supply to the base and watch the collector voltage fall. If the transistor passes these tests it is alive; now, touch the base through a 1K resistor and notice collector noise rise on the scope. That was the AC test. I've worked on transistor circuits for over 50 years, and these tests have always worked for me because when they seem to fail beta is low. How does beta become low; breaking down the b-e junction, dirt accumulation, temperature, time, and life.
Testing the transistor

## Out of circuit testing

Remove the transistor from the circuit for accurate test results.

1. (Base to Emitter)

Hook the positive lead from the multimeter to the to the BASE (B) of the transistor. Hook the negative meter lead to the EMITTER (E) of the transistor. For an good NPN transistor, the meter should show a voltage drop between 0.45V and 0.9V. If you are testing PNP transistor, you should see “OL” (Over Limit).

2. (Base to Collector)

Keep  the postitive lead on the BASE (B) and place the negative lead to the COLLECTOR (C).

For an good NPN transistor, the meter should show a voltage drop between 0.45V and 0.9V. If you are testing PNP transistor, you should see "OL" (Over Limit).

3. (Emitter to Base)

Hook the positive lead from the multimeter to the to the EMITTER (E) of the transistor. Hook the negative meter lead to the BASE (B) of the transistor.

For an good NPN transistor, you should see “OL” (Over Limit).If you are testing PNP transistor, the meter should show a voltage drop between 0.45V and 0.9V.

4. (Collector to Base)

Hook the positive lead from the multimeter to the to the COLLECTOR (C) of the transistor. Hook the negative meter lead to the BASE (B) of the transistor.

For an good NPN transistor, you should see “OL” (Over Limit).If you are testing PNP transistor, the meter should show a voltage drop between 0.45V and 0.9V.

5. (Collector to Emitter)

Hook the postitive meter lead to the COLLECTOR (C) and the negative meter lead to the EMITTER (E) – A good NPN or PNP transistor will read "OL"/Over Limit on the meter. Swap the leads (Positive to Emitter and Negative to Collector) – Once again, a good NPN or PNP transistor should read “OL”.

If your bipolar transistor measures contrary to these steps, consider it to be bad.

You may also be able to use the voltage drop to determine which lead is the emitter on an unmarked transistor, as the emitter-base junction typically has a slightly higher voltage drop than the collector-base junction.

Remember: This test only verifies that the transistor is not shorted or open, it does not guarantee that the transistor is operating within its designed parameters. It should only be used to help decide if you need "replace" or "move on to the next component". This test works on bipolar transistors only – you need to use a different method for testing FETs.


# Transistors
Hfe / B (beta) is the forward transfer characteristic, i.e. transistor gain when used in the common emitter mode. Beta is a static (DC) parameter the DC current gain,which gives a rough idea of the ac gain
Ic = Ib * Hfe
 
Current−Gain − Bandwidth Product: This is the transition frequency describes how the transistor’s current gain is affected by the input frequency. It has a low pass effect, so for example, given 4MHz, signals above this will be attenuated, below this – no change.
 
Base –Emitter on Voltage: Emitter Base Voltage is the maximum voltage that may be applied when the base-emitter diode is in reverse; not conducting. This is generally much lower than a small signal diode in reverse can handle
 
Breakdown voltages:  Indicate maximum voltages allowed before transistor stops working.
Breakdown voltage of V_CE is voltage between collector and emitter with base open

# Distortion types
Fuzz: Hard clipping with a bass boost
Distortion: Hard clipping with a possible bass decrease
Overdrive: Soft clipping using diodes, cutting the bass before, cutting it after processing
Info from https://www.youtube.com/watch?v=MVoPkaqRpCs&list=WL&index=24&t=105s



# Guitar pedal building
## Building steps GGG recommends:
1. Mount the potentiometers. The potentiometers have a small lug at the base of the stem that can be used to hold it in place when it is mounted. We don't use these lugs, we have found them to be unnecessary. Most commercial stompboxes do not use them either. You will need to remove the lug so that the potentiometer can be mounted flush to the inside surface of the enclosure. These lugs break off very easily by just bending it to the side with needle nose pliers or a side cutter. Note in the photo below the lug is not being cut off, but just grabbed with the tool and sort of twisted off to side.
2. Mount the DC Jack. This can be a little tight since it may be directly over a potentiometer, but you can hold the nut in place on the inside of the enclosure and screw it in from the outside to get it started.
3. Mount the populated and pre-wired PCB with the self-stick standoffs.
4. Wire and solder all the connections to the potentiometers, DC jack and switch(es).
5. Mount the Input and Output Jacks and wire and solder them.
6. Solder in the battery Snap. This sequence allows for more space for getting your soldering iron in and out to do most of the wiring before the big input/output jacks get in the way. We have found this sequence to be the easiest way to get the wiring done.


## Design Considerations
Placement of jacks/power etc
orientation of board is that when you take the lid off, you'll see the components.
 
* Usually PCB components are outwards towards removable plate
* DIYGUITARPEDALS: LHS: Input, TOP: Pot, 9V, RHS:Out
* TONEPAD: Same
* GGG: All at top (KayTremolo), All at top (Maestro SuperFuzz etc) -- Input LHS...to RHS Output
* BYOC: Same as TONEPAD, DIYGUITARPEDALS
 
## PCB Mounting
* Start with Double Sided Tape
* Electrical Tape
* Board mounted pots when designing
* Tape on back of pots – pcb (non-component side) to that
* Hardest: Mounting posts
* Potentially best : Smallbear's Bearbox1 http://smallbear-electronics.mybigcommerce.com/the-bare-box-1/
On that note, I use a piece of foam (non conductive) under all my PCB's to make sure the solder side can't touch the enclosure, no matter what happens. It also pads the PCB, making everything fit nice and tight inside...and keeps batteries from moving around.  I think it's a piece of 'egg crate' mattress pad that I cut to make less fat.
If i use double sided tape on the back of the PCB (to protect from shorting), i usually put a dob of hot glue to fix the pcb down to the enclosure and stop it from flapping around inside.  You can also easily remove it as well, the hot glue will snap away from the enclosure without too much effort.
Devi Ever:
Yeah, I've been wrapping my circuits in electrical tape for nearly a decade (having hand built thousands using that lo-fi technique) and NEVER, I repeat NEVER had a pedal returned with any issues because of that.  (it's not like they're free floating.  They are gently hugged between the pots and the lid when closed.  It may not look pretty to some, but it definitely works!  The key is to make sure the board is somehow secured.  I definitely wouldn't trust this method if you had a big empty case and the board was just going to be jostling around willy nilly.

More recently I've had a dozen of my pedals redesigned to have the boards mounted directly to the pots which I've heard people freak out about this more than my electrical tape usage (there fear being that over time the solder connections will vibrate loose or something silly like that), but once again never had a problem and have been doing it for a year now.

Ideally though I'm headed the way of a lot of other boutique builders (and a large percentage of bigger manufacturers) and plan on having practically everything board mounted so that they're easier to assemble, and once again, I have no doubt in my mind they will hold up to long term stress just as well as any other method.
... and yeah, as someone mentioned earlier in this thread, adhesive is a no go with metal and standoffs.  I mean, there are some kind of industrial strength bonding agents, and if you goop enough, you can get a pretty decent fix going, but _that_ is something I definitely wouldn't gamble with.
1. Hoffman
From a reliability point of view, there are no adhesives that really work all that well on metal.  Because of this, my preference is to use countersunk #4 stainless steel screws with aluminum standoffs.  It's not the best looking thing, but it is strong as can be, and the chance of having problems, even in the roughest touring situation, is pretty small.  I also use lock nuts to bolt everything down, so I don't have to go in and tighten anything. 


## Enclosure finishing / Spray Painting
Drill out holes
Add in components / Check component placement
Sandpaper back with 200 grit for a few minutes
Make a few light passes with a colour spray paint (don't go heavy) wait an hour or so between applications
Add on art work / Labelling
Make a 2 passes of acrylic coating .. don't forget the sides. Wait at least 1 hour between coats.
 
Method for Spray Painting
1. Drill Enclosure first
2. 150 grit sandpaper wrapped around a sanding block – sand for a while all corners whole thing –5 minutes.
3. Use Fine then Extra fine synthetic steel wool
4. Spray primer
5. Label enclosure
6. Spray clear coat
 
 
 
Easiest: Spray paint | Permanent Markers | Sealant
Best: Powder Coated box | Water Slide Decal | Sealant + John Cooper Method
 
Method for Spray Painting
1. Drill Enclosure first
2. 150 grit sandpaper wrapped around a sanding block – sand for a while all corners whole thing –5 minutes.
3. Use Fine then Extra fine synthetic steel wool
4. Spray primer
5. Label enclosure
6. Spray clear coat

# Best practices
## Track Widths

* OHS Park's minimum = 6mil
* RG:
It's a complex subject, but in general, for effects, trace widths 0.01"/0.25mm are fine, if a bit fragile. I habitually use 0.025"/ 0.635mm wide traces on a 0.025"/0.635mm grid, but my PCB software is set to alert me when conductors are nearer than 0.010"/0.254mm spacing, so this has the effect of putting traces 0.05"/1.27mm apart for most situations.  I also do not hesitate to drop to 0.012"/0.317mm traces when needed, with the same "warn me when spacing gets under 0.01"/0.25mm". 
 
Power and ground traces should be no less than 0.025"/0.635mm wide, and wider is better. 
 
So, for your question:
- 1mm wide traces for signal and general use is generous. If you can do it with this wide trace, it's fine. Don't hesitate to drop to 0.5mm or 0.3mm if you need to for signals.
- 1mm between traces is WAY generous. I use about 20 mil/0.5mm on average and don't worry until some spots get below 0.01"/0.254mm. 
- the industry wants pads at least 0.020"/ 0.5mm bigger in diameter than the hole. That's very, very minimal. Use 0.062 minimum pads unless there is good reason not to.

 
From <https://www.diystompboxes.com/smfforum/index.php?topic=109208.0>

## PCB Pad Sizes

RG: (He also suggests measuring/ datasheet) The problem with holes too large is that solder has to cover the gap, and too big leaves you prone to bad solder joints. More of an issue with wave solder, I admit, but I have had bum solder joints across too-big holes before.
 
0.030" is a reasonable default. The default size for transistors, DIPs, and 1/4W resistors on down is either 0.028 or 0.025. 0.035 will barely take a 1N400x lead, but it's much easier to assemble at 0.042. I would never go below 0.025 unless for a via.
 
But then the factory that does my board stuffing wanted me to open up all the small stuff holes to 1mm/0.03937, too. And they were hand inserting.
 
The lead-plus-0.010" is that most industry guides say, and I think it was in mil spec, back when there was a mil spec.
 
From <https://www.diystompboxes.com/smfforum/index.php?topic=74168.0>
 
Yep, that's right, go look up the datasheet for the part and it will have mechanical drawings which specify the lead sizes.
Failing that, go to Harbor Freight and buy one of their 6" dial calipers, usually under $20 and measure the leads. Add 0.010" to the lead and make the hole at least that big.
 
From <https://www.diystompboxes.com/smfforum/index.php?topic=74168.0>
 
round leads: add 6 mils to the nominal round lead diameter to get the recommended PCB hole diameter
 
From <https://en.wikibooks.org/wiki/Practical_Electronics/PCB_Layout>
 
"The optimum pad diameter for a through-hole component is twice its finished hole diameter."[14]
 
From <https://en.wikibooks.org/wiki/Practical_Electronics/PCB_Layout>

## Drill bit sizes
3PDT Switch 10 11.94mm
LED Clip 6.5mm 4.98 5.43
LED threaded 7.8mm
16mm Pot 7mm 6.96mm
Power 12 mm 11.94
In Out Jacks 9mm x 9.15mm
Toggle switch 6mm

## Hammond Sizes
Hammond 1590BB - best boxes (geofx)
125B (inbetween size of BB and B) second best / biggest (pedalparts aus youtube … extra height/room)
Powder coated is nicest


# Finishing stompbox - wiring etc

1. Test the PCB board: don’t solder pots — solder wire and tin it, then connect it to bread board and use pre wired pots to test
2. Install foot switch: lock washer goes curving up towards enclosure (inside), on top/ outside enclosure goes the white plastic piece then finally the metal washer.
3. Install mono jack on RHS (output) (when facing the pedal)
4. Install stereo jack
5. Solder footswitch
6. Install and solder LED
7. Install pots and continue

# rhps-control-panel
Software for controlling the screen/lights for a Rocky Horror shadowcast control panel prop

## Overview
My name is Nick Iannone, and in addition to being a software engineer in Milwaukee, WI, I am also a Rocky Horror shadowcaster for [Sensual Daydreams](https://www.facebook.com/groups/45995423803/), where I play Riff Raff. Our ["Sonic Transducer"](http://www.rockyhorror.design/props/printready/sonic-transducer/) prop, aka the Control Panel, is a centerpiece of our prop collection, but it's at least a decade old, falling apart, and not very interactive. We have a few engineers on cast, and we want to rebuild it, and make it lighter, newer, more screen-accurate, and more interactive.

In order to do this, we'll be rebuilding the structure of the Control Panel, with moving cranks, levers, and gauges, as well as the screen and other displays, which will be powered off a standard 120VAC power strip plugged into the theater's outlets and controllable via both our lightboard (for backlighting) and buttons/levers on the device itself.

This project will encapsulate the programming side of the project; due to the need to render video and interface with switches and physical sensors/actuators, we will be using a Linux-compatible microcomputer with video output and digital I/O capabilities (ie. Raspberry Pi or BeagleBone Black). We're avoiding Arduino for now because of the need for video, but we may use it as a breakout board for some of the other devices.

As a side note, this project is also being documented for a possible future Tipsy Talk at ComedySportz in Milwaukee, WI; I will be walking through the design and build process for the control panel's electrical system, and giving a live demo, while drunk off my ass.

## Design Overview
The Control Panel is broken up into several labeled components:

* Sonic Oscillator - Two vertical levers and two vertically-stacked oscilloscope displays. The levers must stay in the upright position until moved down, which will turn on the oscilloscope displays. "Throw open the switches on the Sonic Oscillator!"
* Reactor Power Input - A needle gauge above an 8-segment light-up button panel, in the shape of an umbrella. Three of the buttons should light up when pressed, and stay illuminated; after all three are pressed, the needle gauge should go from zero to oscillating between 45-65% duty cycle. "And step up the Reactor Power Input, three... more... points!"
* Sonic Transducer - A large vertical lever with three mounting arms connected to a single handle. Should be free-swinging, hold position, and not connected to anything electronic. "The Transducer will seduce ya!"
* Monitor - An octagonal port enclosing a square display monitor, with a slot-machine style vertical lever on the right side of the enclosure. Pulling the lever should "change the channel" on the monitor, and shift between a sequence of video clips. "Well, see if you can find him on the MONITOR!"
* Medusa - A vertical lever over a cutout display of a lightning bolt, which should flash green light when the lever is pulled downwards. "You'd better not try to hurt her, Frank Furter!"
* (unlabeled) Wheel - A wheel with a crank handle on it, reminiscent of the crank wheel on a freestanding boat lift. Should spin somewhat freely, but does not need to connect to any electronics. "The Sword of Damocles is hanging over my head!"
* Triple Contact Electro Magnet - A horizontal sliding lever on a track with four discrete stops, the rightmost two being lower than the leftmost two with a downward slope to the track from stop 2-3 and horizontal track from stops 1-2 and stops 3-4, going left to right. Below the track, there are three large vertical pieces, or "electro magnets", which extend out of the panel a few inches, corresponding to the lever hitting stops 2, 3, and 4. "Shall we enquire of him in person?"
* (unlabeled) Back panel - The obstructive glass paneling which makes up the backing of the control panel itself. Contains a backlight against a white plastic(?) backing which provides soft, consistent illumination. Should be able to be turned on and off from the lightboard, and should not be connected to any other electronics. Is replaced by a bright, blinking horizontal fluorescent light behind the space between the Monitor and the Triple Contact Electro Magnet during the Creation scene, before "Sword of Damocles".

### Electrical Components

* Sonic Oscillator
  * Switches
    * Potentiometers & Wiring
  * Oscilloscopes
    * Signal Generators
    * Cheap Oscilloscopes
* Reactor Power Input
  * Gauge
    * Large Needle Gauge (Analog Voltage)
    * Low-Amp Analog Voltage Output
  * Button Panel
    * Lights
    * 3 small locking switches
    * Microcontroller with analog outputs
* Sonic Transducer
* Monitor
  * Display
    * BeagleBoard Microcomputer
    * Display cord (HDMI?)
    * Flat-screen monitor
  * Lever
    * Potentiometer and wiring
* Triple Contact Electro Magnet
  * TODO
* Back Panel
  * TODO
  
### Mechanical Components

TODO

### Program Design

TODO

## Build

TODO

## Testing

TODO

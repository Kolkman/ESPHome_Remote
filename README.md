# Reliable Harmony

The use case is:

I want a one remote solution.
 
I have the following hardware:

* A Marantz NR1609 AV receiver
* A Sony Bravia television (KD-43XF8505)
* An Amino Aria A710 setup box for Canal+
* A Logitech Harmony One remote

After ordering Canal+ I had to watch TV through the setup box. Juggling 3 remotes is not what I want so I tried the following approach: 

I programmed the Logitech for several activities which turn on and off the various devices and put them on the right inputs to work. "Watching TV" would turn on all devices and send all commands needed to get the TV use the setup box as the input and use the remote to change channels, volume, and send other commands to the various devices. 

That is a very fragile setup. So when I realized that there is a Canal+ app for the Bravia and that both the Marantz and Bravia can be controlled through HomeAssistant using the APIs instead of IR. I came to the following 'One Remote' solution.

* Use an ESPHome programmed device with an IR receiver to interface with the TV and AV APIs through Home Assistant.
* Program the Harmony to only work with the ESP (i.e. with remote IR codes that have nothing to do with the original hardware.

For that I programmed the Harmony with IR codes of a TV and an AV Receiver, other than the sony and marantz, that have well defined protocols.  For the 'fake TV' I programmed the logitech to act as a remote for a Samsung qe50q64c, for the 'fake AV' the remote thinks it is talking to a SonySTR-K520P.

When the ESP sees one of these codes it will call the Bravia's or Marantz' API.

Hardware is trivial. A KY-022 remote receiver is connected to pin

This repository contains some files and notes relevant to this setup. 

Some relevant documents

* [Home Assistant Bravia TV](https://www.home-assistant.io/integrations/braviatv/)
* [Home assistant Denon AVR
](https://www.home-assistant.io/integrations/denonavr/)
* [Denon IR Codes](https://assets.denon.com/documentmaster/uk/avr3313_ir_code_v01.pdf) and [API](https://www.heimkinoraum.de/upload/files/product/IP_Protocol_AVR-Xx100.pdf)
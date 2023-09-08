# Arcade Idolm@ster - Card Reader Emulator v1.0

## Behaviour

The main difference between the original script and this one, is that Akemas (Arcade Idolm@ster) uses two cards, and that in order to play a new game, it's necessary to reproduce the card eject state.

These two cards are:

- "Producer card" which holds player information (P)
- "Unit card" (U) that holds the data about the character you're Producing

It is necessary for the script to have a function to receive an eject command, then enter the eject state, and finally insert any card of any of the two types at an arbitrary timing.

## Use

The script was programmed in Python3 and requires Pyserial.

```bash
pip install pyserial
```

An example of the command to run it:

```bash
imas_card.py -cp COM3 -fp IDMSFILE_USER.hex
imas_card.py -cp COM3 -fu IDMSFILE_HARUKA.hex
```

The first sticking card will be the one you specified with "-fp".

The -fp is assumed to be a P-card and the -fu is assumed to be a U-card.

Specify a filename for your card file. If the file doesn't exist or is blank, a new card must be purchased when starting the game. If the file has data it will be automatically loaded at the point the game asks if you have a card.

You can restart the script and load different card data in game over mode.

### Wiring (for the Chihiro, not sure about the Sys256)

- CN5 is an 8-pin header on the Chihiro and drives both the NAMCO FFB unit and the card reader/writer unit, so keep that in mind if you ever try to wire up one of the FFB units as well. Normally the FFB would use the ground at Pin 3 while card r/w uses ground a Pin 8. However if you're just wiring in for the card emulator, you can use a 3 position housing and connect sequential pins 3-5.
- CN5 on Chihiro to Female 9-pin D-sub that connects to USB Serial Adapter (TU-S9):
- Pin 3 [or 8] (GND) - Pin 5 (GND)
- Pin 4 (TXD) - Pin 2 (RXD)
- Pin 5 (RXD) - Pin 3 (TXD)

## Data

Cabinet Name: Rewritable stage

System Board: System 246/256

Other Games that use this Card Reader:

- Dragon Chronicle
- Minna de Kitaeru Zenno Training

## Notes

Card command constants referenced from Dolphin emulator Triforce branch.

Serial interface referenced from `jpnevulator.py` script.

## Credits

This is **not my work**, I only reuploaded and gathered the data for easy acess and sharing. If you're anyone involved with this script and want me to take it down, just DM me.

**Card Reader Emulator** originally programmed by [winteriscoming](https://www.arcade-projects.com/threads/naomi-2-chihiro-triforce-card-reader-emulator-initial-d3-wmmt-mario-kart-f-zero-ax.814/).

Modified and posted by [sakiranorium](https://www.arcade-projects.com/threads/naomi-2-chihiro-triforce-card-reader-emulator-initial-d3-wmmt-mario-kart-f-zero-ax.814/post-219918) at the [Arcade Projects forum](https://www.arcade-projects.com)

Special thanks to: MetalliC

### jpnevulator.py version 2.1.3

Copyright (C) 2015 Philipp Klaus

*This is free software.  You may redistribute copies of it under the terms of the [GNU General Public License](http://www.gnu.org/licenses/gpl.html). There is NO WARRANTY, to the extent permitted by law.*

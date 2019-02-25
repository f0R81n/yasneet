# ysneet
## Introduction

This project has grown out of a few things that I have been working on for the last few years for embedded processor design and development. For my paying job I do a lot of work with a range of embedded processors, these days predominantly the ARM family of microcontrollers. I have been using ARM based microcontrollers all the way back to 2000 when they were a lot less common. At the time we developed a system around the Atmel AT91 devices. I had a brief look on Wikipedia and the family that we used dosen't even rate a mention in the Atmel ARM entry. It had no internal FLASH memory, 2 UARTS and a Timer... thats pretty much it! The debugger was a rather painful affair based on a parallel port bit bashed device from Macraigor Systems. For compilers we used Greenhills, Metaware and a very early version of GCC that was ARM only, no THUMB (so 32bit code generation only).

It has all changed now. If you go to Digikey, Mouser, et el and look at microcontrollers there are well over 2500 different ARM based devices from over a dozen manufacturers (and that's with the compaction of the semiconductor industry over the last few years).

Another big interest in my life has been Analog Synthesizer design & development and recently there has been a collision of the two interests in a number of EuroRack modules using microcontrollers, in particular the designs of Oliver Gillet of [Mutable Instruments](https://github.com/pichenettes/eurorack). The fantastic thing about Oliver is that he has placed his designs on GitHub for other people to *tweek*... One of the designs that has benefitted from this is [Ornaments & Crime](https://github.com/mxmxmx/O_C).

The Ornaments & Crime board makes use of the [Teensy 3.2](https://www.pjrc.com/store/teensy32.html) as its processing core. This is a nice little board that effectively breaks out an ARM Cortex M4 into a 28 pin dil style package. As usual I decided to tweek on a tweek and started hacking the O&C code for the fun. I quite quickly got a lot frustrted with the Arduino libraries for the Teensy and the whole development process for the O&C code. The Arduino is great for relatively simple things but I felt that this was probably a bridge to far as the O&C code is really quite complex. I take my hat of to the developers of the O&C code but the process wasn't for me... The Teensy hardware is also a bit painful when things get complicated as there is no debug interface -- the board uses a curious scheme with a second microcontroller to manage uploading the code and no access to the ARM debug pins... The newer Teensy boards do provide better debugging fascilities but they are all larger boards and I am intinsically happy with the size and general functionality of the 3.2.

That spawned the first Ysneet board which is effectively a Teensy 3.2 with:
- a faster processor with a floating point processor (never sure why the original was just an M4 and not an M4F)
- a more robust USB connector -- not a fan of micro USB connectors as they seem to have a limited mating cycle count
- a SWD debug interface
- a switchmode power supply for increased efficiency and higher input voltage range
- a larger component footprint for hand soldering (if relatively careful)

After having a bit of fun with that I decided that what I really needed was fast double precision floating point for some chaotic oscillators I was fiddling with - so now we need an M7. There are two possible M7 ARM devices in a 64pin TQFP package, one from Atmel (well Microchip) and one from STMicroelectronics. Might as well try both? why not? as board is tiny OSHPark will make it for you for $5 US and ship it to you for free! even in Australia!!!

Well why stop there...

## Current Devices State

OK so some of these are a bit *pie in the sky* but maybe we will get a few of these going:

| ID            | Ver | Manufacturere         | Core  | Build Status | Test Status     |
| ------------- | -|------------------    | ----- | ------------ | --------------- |
| DBG           | 1|NXP (was Frescale)    | M4F   | 100%         | 50%             |
| SAM7          | 1|MicroChip (was Atmel) | M7    | 100%         | 20%              |
| STM7          | 1|STMicroelectronics      | M7    | 100%         | 20%              |
| EFM           | 1|Silicon Labs            | M4F   | 100%         | 0%              |
| XMC           | 1|Infineon                | M4F   | 100%         | 0%              |
| TMC           | 1|Texas Instruments (Tiva)  | M4F   | 100%         | 0%              |
| MSP           | 0|Texas Instruments (MSP432) | M4F   | 0%         | 0%              |
|APLO| 0|Ambiq|M4F|0%|0%|
|ADUC|0|Analog Devices|M4F|0%|0%
| MAX           | 0| Maxim | M4F | 0% | 0% |
| NUV           | 0| Nuvoton               | M4F   | 0%           | 0%              |
| GIG           | 0| Gigadevice            | M4F   | 0% | 0% |
| BFIN          | 1 |Analog Devices        | BF70x | 100% | 0% |
| PIC           | 0 |Microchip             | PIC32 MZ | 0% | 0% |
| DSPIC         | 0| Microchip             | DSPic33 | 0% | 0% |
| AVR           | 1|Atmel                 | AVR32 | 100% | 0% |
| SI5           | 0|SiFive                | FE310 | 0% | 0% |
| 430           | 0|Texas Instruments     | MSP430 | 0% | 0% |
| CF1            | 0|NXP (was Freescale)   | ColdFire V1 | 0% | 0% |
| RX            | 0|Renesas               | RX62N | 0% | 0% |

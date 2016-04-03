# Project Description #

SDR-Widget is an interface based on the Atmel AT32UC3A3 microcontroller that provides the following functionality to SDR circuits such as the SoftRock.  A branch of the project called audio-widget provides a USB-I2S module and various Analog Boards (AB) for audiophile USB-DAC playback.

sdr-widget:

  1. High quality audio using the USB Audio Class standard (UAC1 and UAC2)
  1. Capture and Playback at 48/96/192khz 24 bit under uac2 for OSX, Linux and Windows
  1. (For Windows, a uac2 ASIO driver is available)
  1. PTT control
  1. Si570 control
  1. SWR metering
  1. PWR metering
  1. PA Heatsink Temperature metering
  1. PA bias adjustment
  1. LCD display
  1. Rotary Encoder Input
  1. Filter bank switching control
  1. CW paddle

The interface also aims to be used as a general platform for future experimentation with SDR peripherals.

audio-widget:

A branch of the widget, called the audio-widget, provides a USB-I2S module for mating with various Analog Board (AB) designs featuring different DAC, IV conversion, buffer/amplification, and power supplies.  So far we have AB1.1 (ES9023), USB9023 (ES9023) and USB5102 (PCM5102) produced.  AB1.12/AB1.13 for experimenters (AK4430, ES9012) are available.

The audio-widget can be enumerated as a USB Audio Device Version 1 (uac1) or USB Audio Device Version 2 (uac2).  uac1 is natively supported by all OSes, but the audio-widget is limited to 44.1/48khz 24 bit playback.  uac2 is natively supported by OSX and Linux, and you have playback at 44.1/48/88.2/96/176.4/192khz 32 bit.  Windows does not support uac2 natively.  We have a Windows uac2 ASIO driver that you can use to playback 44.1->192khz 32 bit using some player software (such as Foobar2000 with ASIO plugin, and JRiver).

For descriptions and photos of the hardware and other info, see:

sdr-widget:

http://sites.google.com/site/lofturj/sdr_widget

audio-widget:

https://groups.google.com/group/audio-widget?hl=en

http://www.yoyodyneconsulting.ca/pages/Audio_Hardware.html

http://www.qnktc.com/usb.php

Instructions for flashing firmware, firmware images (.elf files) etc. can be found in the Download area of this site.  There are instructions and tips in the Wiki area of this page as well.  See also:

https://github.com/amontefusco/sdr-widget/blob/audio-widget-experimental/AW_readme.txt

If you would like to participate in the hardware or firmware development request to join the sdr-widget Google Discussion Group.

The firmware source files are hosted at github.  (This is for EXPERTS only, not for casual users):

git://github.com/amontefusco/sdr-widget.git

Note that the above git://...... is NOT a web link.  It is NOT http:// so you CANNOT click it and expect it to work.

You need to be an experienced user and you must know how to use git before you can work on the source code.  Would be developers please contact us (alexlee188 att gmail dott com)

The master branch is for sdr-widget.  The audio-widget branch is for audio-widget.

The latest cutting edge development for audio-widget is in audio-widget-experimental branch.


# Project Status #

  * 2009.06 - Definition phase
  * 2009.08 - Design phase
  * 2009.10 - Prototype Pcb layout phase
  * 2009.12 - Successfully got test code to load via USB and run on the SDR-Widget-Lite
  * 2010.01 - Firmware development started
  * 2010.04 - Composite high speed USB device with 4 interfaces
> > Audio capture @48khz 24bits stereo demonstrated.
> > I/Q demodulation demonstrated with widget-lite + Mobo v4.3 + SR v6.3
> > Mobo interface with DG8SAQ emulation.
> > ALPHA board testing ongoing.
> > BETA board design started.
  * 2010.05 - Firmware implementation of USB Audio Class v2 standard ongoing.
> > Demonstrated 96khz 24bit stereo capture.  Now working on 192khz sampling.
> > Widget-lite Alpha-2 kits are sold out.  Alpha-2 is expected to
> > have better noise performance and ENOB than many commercial sound cards
  * 2010.07 - Continued development of two branches of firmware, UAC1 for compatibility
> > with Windows, UAC2 for Linux kernel 2.6.36 and Mac OSX.
> > We have demonstrated 192khz 24bit stereo capture with UAC2 branch, both
> > under Linux kernel 2.6.35rc3 and Mac OSX Snow Leopard.
> > Widget-lite-alpha-2+ kits with both capture and playback at 192khz 24bits
> > are sold out.
  * 2010.08 - Widget-lite-alpha2+ kits being tested.  We will announce the availability
> > of the BETA kits when ready.  BETA will have all difficult to solder
> > surface mount parts pre-soldered.

  * 2010.09 - UAC1 branch firmware with both capture and playback capabilities
> > demonstrated.  Asynchronous OUT playback tested in Linux and in OSX.
> > In WinXP it causes Blue Screen of Death (BSOD).  When connected to
> > Softrock and Mobo, full transceiver (both receive and transmit) functions
> > demonstrated.  When configured for Synchronous OUT playback, it works
> > in WinXP without any crash.  (Of course, the quality of playback audio
> > will not be as good as Async OUT.)

  * 2010.10 - Widget-lite-BETA is being planned and it should ship by Thanksgiving.


> About 100 sets of BETA will be made available.  We are deciding whether
> to have the BETA fully assembled.  The remaining firmware development
> task is the UAC2 ASYNC OUT with rate feedback playback at 48/96/192khz.

  * 2010.10 - Firmware for UAC2 SYNC OUT playback 48/96/192khz 24 bit stereo working.
> > So under Linux 2.6.35 or later and OSX, the widget has full 48/96/192khz
> > 24 bit stereo capture and playback capability.


> We are planning for two BETA versions.  (1) widget with full sdr
> control connectivity and 20x4 LCD connectivity; (2) Audio Widget
> with only soundcard functions, but with an upgraded DAC for audiophile
> playback.  Both will be fully assembled.

  * 2010.11 - Firmware for UAC2 Async OUT with rate feedback, 48/96/192khz 24bit stereo
> > duplex capture and playback demonstrated.  Testing with Windows UAC2 drivers
> > pending.  Started work on firmware to use the HPSDR protocol instead of
> > UAC, for interfacing with SDR software such as GHPSDR3 and PSDR that can
> > communicate with Ozy (of the HPSDR project).  This way, the widget will
> > emulate an Ozy device with a Janus card.  96/192khz operation should be
> > possible as there are no Windows UAC1 driver limitations.
> > Early firmware running the HPSDR protocol to emulate Ozy/Janus demonstrated.
> > Using ghpsdr3 software, 192khz 24bit Rx demonstrated.

  * 2011.01 - The Pebble SDR software (developed by Richard N1DDY) running in Windows
> > has added support for the widget with the hpsdr firmware.  Rx at 48/96/192
> > 24 bits has been demonstrated.  The sampling rate can be switched on-the-fly
> > within the Pebble GUI.


> Design of the audio-widget has started.  It will have:

> (1)  A USB-I2S module, which provides the USB interface to the PC and
> > the I2S interface, I2C interface, and 10 gpio pins for the ADC/DAC;


> (2)  Several Analog Boards (AB), the 1st AB being designed will feature
> > the ES9022 DAC.  Other AB's will feature other DAC's, different
> > IV conversion and output buffer/amp etc.  One AB will feature an FPGA
> > for multichannel and digital oversampling/filtering/crossover function;


> (3)  Power Supply Boards, which will provide the super quiet +/-9V
> > The first PS Board will likely feature bipolar DC-DC coversion, Wenzel
> > Finesse regulator etc.  Another PS Board will use the USB +5V to
> > charge LiFePO4 battery or supercap when not in operation.  Then the
> > bettery/supercap will supply the AB during operation.

  * 2011.02   The sdr-widget BETA have all been sold out.  Some info about the BETA
> > is listed below.  We are waiting for feedback from the 90+ BETA users
> > before deciding on the production run.


Hardware Features:

> - Compact 3" x 2.5", 2 board stack. 3.5mm audio connections.
> - Powered from the USB port, no external power supply needed
> - 24-bit AK5394A ADC - the premier audio ADC in commercial use today
> - CS4344 24-bit DAC
> - I2C control bus
> - 16-bit LCD panel interface (configured for 4-bit) with drivers for
> HD44780 based 4-line displays
> - Connector for quadrature rotary encoder input (with push switch)
> - 3 optocoupler buffered inputs
> - 3 mosfet 'contact' outputs
> - Firmware update via USB port
> - JTAG port (connector not mounted)
Software Features (either present or coming soon)
> - USB composite device with audio I/O, control and CDC channels
> - Supports USB Audio class 2 (480mbs) on the latest Linux kernel as well
> as the latest Mac OS
> - Support 24-bit 48k/96k/192k sample rates on Linux and MacOS
> - Support USB Audio class1 on Windows at 48k sample rate. NOTE: Windows
> does not support UAC2
> - Has an integrated CDC, Communications Device Class, channel for debug
> messages
> - A superset of the DG8SAQ control interface
> - 4-line LCD message engine
> - Menu system with selection control via external rotary encoder and
> switch.
Mark J Dulcey eloquently explains the issues with Windows data rates:
" The widget supports the industry-standard UAC2 (a standard for audio
over USB); UAC2 offers sample rates up to 192KHz and multiple channels
operating over a high-speed USB (480MHz) interface. Mac OS X and recent
Linux kernels support UAC2; Windows does not.
UAC1 firmware is also available for the widget. That's the older USB
audio spec designed for full-speed USB (12MHz), and it supports
full-duplex stereo at sample rates up to 48KHz. USB audio devices that
support higher speeds on Windows use custom Windows drivers; there is
currently no such driver for the widget, which was intended to work
without any need for such drivers. "
---
The software is open source and there is nothing stopping the creation of a
custom driver that will allow higher transfer speeds under Windows.  The
HPSDR USB protocol has been implemented.

**audio-widget ALPHA**

> We are preparing for the fab of the audio-widget ALPHA, which has the
> USB-I2S module and the Analog Board (AB-1).  AB-1 has the ES9022 DAC
> and the whole widget is USB powered.  The output is 2Vrms and can drive
> a headphone directly.  If you are interested in the audio-widget ALPHA
> you should join the audio-widget group now:

https://groups.google.com/group/audio-widget?hl=en

  * 2011.03  A unified firmware that works for both the sdr-widget and audio-widget,
> > with feature set that can be selected at run time (and then stored in
> > non-volatile flash user page) so the feature set will be used at
> > subsequent resets, is available:


> git://github.com/amontefusco/sdr-widget.git

> There are 3 branches under active development:  master, audio-widget-win and audio-widget-nik

> The selectable features include:

board =  none widget usbi2s usbdac test

image =  flashyblinky uac1\_audio uac1\_dg8saq uac2\_audio uac2\_dg8saq hpsdr test


in =  normal swapped

out =  normal swapped

adc =  none ak5394a

dac =  none cs4344 es9022

lcd =  none hd44780 ks0073

log =  1sec 2sec 4sec

  * 2011.03  audio-widget USB-I2S module and AB-1 ALPHA boards are being manufactured.

  * 2011.05  The prototype boards of USB-I2S module + AB-1 are sold out.  A single
> > board USBDAC version with the ES9023 DAC is still available for order.
> > Contact George.

  * 2011.07  AB-1.1 is an improved AB-1 audio-widget with better sound quality.  Email Borge to order.  USB9023 Rev A is an improved USB9023 with better sound quality.  Email George to order, or visit his Yoyodyne Consulting website.

  * 2012.03   The current run of sdr-widget has all been sold out.  George may have
> > another run in 3 month's time.


> AB1.12 for experimenters is being developed by Borge.

> A Windows uac2 ASIO driver is available for the audio-widgets.  It is
> developed by Nikolay is an open source design.  The Windows installer
> (drivers and WidgetControl.exe) is available in the Download area.
> The source code is in a git repository.

> So under Windows (and OSX and Linux), 44.1 -> 192khz 32 bit playback
> is now possible.

  * 2012.08   George is taking pre-orders for a run of sdr-widget.  See his website.

> Borge is selling AB1.12 and AB1.13.  See his website.

> Nikolay's open source Windows uac2 ASIO driver supports BOTH capture and
> playback, from 44.1->192khz 24 bit for the sdr-widget.  For audio-widget,
> it supports 44.1->192khz 32 bit playback.

> Borge and others are designing the next generation of Analog Boards to
> mate with the usb-i2s module.  Features include galvanic isolation of
> the DAC from the uController and USB, improved power supplies to the
> clocks and analog stages, sampling rate display led's and hardware
> volume control.
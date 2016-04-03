# Introduction #

This page is a work in progress. Please copy your Win7 hints here.


# Cleanup! #

First of all: Clean up old drivers!
Loftur recommends this link: http://www.tech-recipes.com/rx/504/how-to-uninstall-hidden-devices-drivers-and-services/

You may also benefit from reading this page on automatic driver installation: http://www.addictivetips.com/windows-tips/how-to-disable-automatic-driver-installation-in-windows-vista/

# Select Playback Device #

It might seem totally mundane, but don't forget to right-click on the little bottom-right loudspeaker icon and actively select playback device. Frequently, the most recently added audio device takes over, but not always.

# Atmel Flip #

The downloads section now includes a batch file kit for programming and testing. See readme.txt in [Add\_to\_flip345\_bin.zip](http://code.google.com/p/sdr-widget/downloads/detail?name=Add_to_flip345_bin.zip&can=2&q=#makechanges).

Atmel Flip is found at http://www.atmel.com/dyn/products/tools_card.asp?tool_id=3886

Go ahead and install it as usual. You must read and understand http://www.atmel.com/dyn/resources/prod_documents/doc7745.pdf But the USB driver must be replaced by a signed driver.

To make Atmel Flip work with a signed driver, fetch one at
http://www.avrfreaks.net/index.php?module=Freaks%20Files&func=viewFile&id=3842&showinfo=1
For the remainder of this text, it is assumed that downloading and unzipping it creates the folder "C:\Program Files (x86)\Atmel\Flip 3.4.2\usb\driver"

After you install the signed driver, unplug the board and plug it back in with the program button pushed down. Keep an eye open in Device Manager to check if it enumerates.

# Widget Control #

Go to the Downloads section and get your copy of WidgetControl\_setup.exe. In order to make it work after installation, you also need the SDRWDGT-USB-Driver-1.2.1.0 driver. Install it manually by running hdwwiz from cmd, then point to the folder you unzip it to. You may or may not need a reboot. You will also need the AUDWDGT-USB-Driver-1.2.2.0 driver after running Widget Control. Drivers are included in file Drivers\_from\_Fred\_20111223.zip in the Downloads section

# Deep Memory #

Windows 7 will remember a lot about your hardware. If it doesn't work as expected, start from the top of this list. You may also want to try recompiling your code with a different USB pid and see if it works better as something _not_ remembered by Windows.
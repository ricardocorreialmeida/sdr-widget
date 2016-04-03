# Introduction #

This text assumes you're on a Windows system.

Make sure Atmel Flip is up and running on your system. You will need the batchisp.exe program from Flip's bin folder. See page [Win7\_64\_setup](Win7_64_setup.md).

The downloads section now includes a batch file kit for programming and testing. See readme.txt in [Add\_to\_flip345\_bin\_20120115.zip](http://code.google.com/p/sdr-widget/downloads/detail?name=Add_to_flip345_bin_20120115.zip).


# Atmel Flip #

Atmel Flip setup on Windows 7

First of all, Atmel Flip is not easy to install. There are several prerequisites
and manual steps you have to go through.

1  - Download the latest firmware from http://code.google.com/p/sdr-widget/downloads/list

2  - Install a Java Virtual Machine from http://java.com/en/download/index.jsp

3  - Install C++ runtime from Microsoft: http://www.microsoft.com/en-us/download/details.aspx?id=5555

4  - Install Atmel Flip 3.4.5 from http://www.atmel.com/dyn/products/tools_card.asp?tool_id=3886 This text assumes you install to "C:\Program Files (x86)\Atmel\Flip 3.4.5"

5  - Copy files from Add\_to\_flip345\_bin.zip to folder "C:\Program Files (x86)\Atmel\Flip 3.4.5\bin"

6  - Do the following. Ignore and approve any messages about driver not being signed. Start, Run, hdwwiz.exe, Next, Install the hardware ... manually, Next, Show All, Next, Have Disk, Browse to "C:\Program Files (x86)\Atmel\Flip 3.4.5\usb", Choose "atmel\_usb\_dfu.inf", Open, OK, Select "AT32U3A3", Next, Next, Finish

7  - Reboot (may or may not be necessary)

8  - Plug in Audio Widget USB Device.

9  - Hold Prog, click and release Rest, release Prog

10 - You may or may notreceive messages about lacking drivers for "DG8SAQ-I2C". Please ignore them.

11 - Windows should now be able to find the boot loader in the MCU. To verify: Start, Run, devmgmt.msc, look for Atmel USB Devices

12 - To program devices use the Flip installation and the Add\_to\_flip.. package: Start, Run, cmd.exe, cd "C:\Program Files (x86)\Atmel\Flip 3.4.5\bin", "prog widget.elf" Substitute "widget.elf" with the compiled firmware file you wish to upload to the Audio Widget. This is the file from step 1.

13 - Expect an output like this in your cmd window:
```

C:\Program Files (x86)\Atmel\Flip 3.4.5\bin>batchisp -device at32uc3a3256 -hardw
are usb -operation erase f memory flash blankcheck loadbuffer widget.elf progra
m verify start reset 0
Running batchisp 1.2.5 on Tue Jul 31 19:44:26 2012

AT32UC3A3256 - USB - USB/DFU

Device selection....................... PASS
Hardware selection..................... PASS
Opening port........................... PASS
Reading Bootloader version............. PASS    1.0.3
Erasing................................ PASS
Selecting FLASH........................ PASS
Blank checking......................... PASS    0x00000 0x3ffff
Parsing ELF file....................... PASS    widget.elf
WARNING: The user program and the bootloader overlap!
Programming memory..................... PASS    0x00000 0x1c43f
Verifying memory....................... PASS    0x00000 0x1c43f
Starting Application................... PASS    RESET   0

Summary:  Total 11   Passed 11   Failed 0

C:\Program Files (x86)\Atmel\Flip 3.4.5\bin>
```
# 1 - Obtain an .elf file #

You may have obtained or downloaded an .elf file. That saves you the git pull and compilation run.

If you need to compile code the best option is to use Cygwin. After downloading and changing to the audio-widget firmware branch (see page [gitRepository](gitRepository.md), do "make clean audio-widget". If you use an integrated editor and Atmel compile tool, make sure it generates .elf.

# 2 - Prepare the board #

To boot into the bootloader do like this:
**Press and hold the Prog button** Press and release the Reset button
**Rlease the Prog button**

# 3 - Run batchisp.exe #

Assuming you want to upload "widget.elf" to the kit run the following command in a cmd window from the bin folder of the Atmel Flip installation (one line):
```
batchisp -device at32uc3a3256 -hardware usb -operation erase f memory flash blankcheck loadbuffer widget.elf program verify start reset 0
```

Alternatively, make yourself a prog.bat file the bin folder of Atmel Flip. The file should contain the following code:
```
batchisp -device at32uc3a3256 -hardware usb -operation erase f memory flash blankcheck loadbuffer %1 program verify start reset 0
```
Then, after pressing the buttons the right way, the command simplifies to:
```
C:\Program Files (x86)\Atmel\Flip 3.4.2\bin>prog widget.elf
```

# 4 - Reboot #

This will happen automatically after running prog.bat

# 5 - Something failed #

You may need to locate an Atmel JTAG ISP mkII kit to debug and reload the bootloader.....
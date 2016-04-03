# Introduction #

This is from Alex's mail on March 30.

With great contributions from a various developers, including Roger,
Andrea, Loftur etc., the Unified firmware is now working quite well,
and I encourage all widget users to start flashing the Unified
firmware instead of the earlier individuall firmware versions.

The source code of the Unified firmware is in a git repository. See the [git repository wiki page](gitRepository.md).

There are two main branches that have active development:

  * master for sdr-widget
  * audio-widget for audio-widget (also works for sdr-widget for playback only.  With additional features for audio-widget boards)

Alex will upload .elf files built from the above two branches to the code page periodically.  The latest .elf files are called:

  * widget.elf built from master
  * audio-widget.elf built from audio-widget


# Prerequisites #
You will have to install Python26 with some add-ons. You will have to install python26, wxpython, pyusb (pre 1.0) and pythoncard. For Windows, use 32-bit packages. Install files are presently found at:
  * http://www.python.org/download/releases/2.6.6/
  * http://www.wxpython.org/download.php
  * http://sourceforge.net/projects/pyusb/files/PyUSB%200.x/
  * Windows: Get PythonCard-0.8.2.win32.exe from http://pythoncard.sourceforge.net/windows_installation.html
  * Linux (untested): http://pythoncard.sourceforge.net/linux_installation.html


# Configuration #

After flashing the firmware, you need to use the WidgetControl.py GUI
tool to setup the feature selections.  The GUI tool works under both
Windows and Linux. The default feature set is for sdr-widget
board, UAC1 audio, normal IQ orientations, AK5394A and CS4344 chips.
This will work in all Operating Systems including Windows.

Note:  if you are running under Windows do NOT select UAC2 features,
as Windows does not support UAC2.

The equivalent of demo\_UAC1\_x\_v087\_WinXP is the uac1\_dg8saq image.
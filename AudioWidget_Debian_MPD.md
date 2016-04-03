# Step 1: Check/upgrade kernel version #
**on terminal run:
```
 uname -a
               Linux debian 2.6.32-5-686 #1 SMP Mon Jan 16 16:04:25 UTC 2012 i686 GNU/Linux
```**

**check if kernel is greater than 2.6.38 if not make yourself root:**

```
su 
```

**backup in case something goes wrong**

```
cp /boot /root -R
```

**edit sources file
```
nano /etc/apt/sources.list
```**

> add at the end of file:
```
 deb http://backports.debian.org/debian-backports squeeze-backports main
```

**update and search for kernels:
```
apt-get update
apt-cache search linux-image- --names-only

                        .
			.	
			.
			linux-image-3.2.0-0.bpo.1-686-pae - Linux 3.2 for modern PCs
			linux-image-3.2.0-0.bpo.1-amd64 - Linux 3.2 for 64-bit PCs
			linux-image-3.2.0-0.bpo.2-486 - Linux 3.2 for older PCs
```**

**choose the appropriate kernel image and run:**

```
apt-get install -t squeeze-backports linux-image-3.2.0-0.bpo.1-686-pae
```

```
reboot
```

# Step 2:  [Reflash AW board](http://code.google.com/p/sdr-widget/downloads/detail?name=Programming%20widget%20firmware.txt&can=2&q=#makechanges) #

**make sure the board is in UAC2 mode ( red led) and run:
```
aplay -l
			card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  			Subdevices: 1/1
  			Subdevice #0: subdevice #0
			card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  			Subdevices: 1/1
  			Subdevice #0: subdevice #0
			card 1: DG8SAQI2C [DG8SAQ-I2C], device 0: USB Audio [USB Audio]
 			Subdevices: 1/1
  			Subdevice #0: subdevice #0
```
DG8SAQI2C  is the card you are looking for - in this case**card id**is 1**

# Step 3: [Install MPD](http://mpd.wikia.com/wiki/Install) and  [configure](http://mpd.wikia.com/wiki/Configuration) #

**after you configure mpd
```
 nano /etc/mpd.config
```**

scroll down to audio\_output section and replace with following:
```
               audio_output { 
		    type            "alsa" 
    	            name            "My ALSA Device" 
      	 	    device          "hw:1,0"   
                    auto_resample   "no"
	          }
```
replace "1" from the above with your **card id**

That's it !
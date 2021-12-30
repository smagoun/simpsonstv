These python scripts are used to make the Desktop Simpsons TV work.

You can find a complete build guide [here](https://withrow.io/simpsons-tv-build-guide)

---

Additional notes for Waveshare 2.8" LCD and USB Audio output:

## Bill of Materials
* Raspberry Pi Zero WH
* Waveshare 2.8inch Capacitive Touch Screen LCD for Raspberry Pi 480×640 
* Sabrent USB External Stereo Sound Adapter
* 3.5mm 90 Degree Right Angle Male Plug to Bare Wire Open End TRS 3 Pole Stereo 1/8" 3.5mm Plug
* Adafruit Mono 2.5W Class D Audio Amplifier - PAM8302 PID: 2130
* Adafruit Speaker - 40mm Diameter - 4 Ohm 3 Watt PID: 3968
* Adafruit USB Micro-B Breakout Board PID: 1833
* Micro USB Male to USB-A female adapter - from CanaKit Pi Zero Wireless Starter Kit (for USB audio adapter)
* 3D printed parts: https://corvallis3d.com

## Build notes:
* Use the [Legacy Raspberry Pi OS](https://www.raspberrypi.com/software/operating-systems/#raspberry-pi-os-legacy) to get support for `omxplayer`
* Unlike the iUniker display, the Waveshare display can plug directly into the Pi Zero WH
* While working with GPIO audio, I tried to use pin 19 for audio. This requires `dtoverlay=audremap,enable_jack,pins_18_19` in `boot/config.txt` This produces audio output, however pin 18 is also used by the screen (backlight control) so pin 18 has to be reset once audio has been initialized.
* Originally I followed the build guide for audio. However the audio from the GPIO had a loud squeal on it. I didn't try 
putting filters on the audio; instead I switched to USB audio. The USB audio signal was much cleaner, but fitting the 
cabling was a bit tricky. It all fit, but I had to cut some of the strain relief off the USB cable in order to get it 
to bend tightly enough to fit.
* At first the Waveshare screen seems to fit perfectly in the 3D-printed case, however the screen isn't centered in the
opening. Next time, cut down some of the interior framing on the screen to allow the screen to shift a bit more away from
the edge (about 1/4" is enough)
* The Adafruit USB Micro-B Breakout Board doesn't fit between the ridges to support the USB port. I cut the ridges
down with a hobby chisel to allow the breakout board to fit.

## References:
* Original build guide: https://withrow.io/simpsons-tv-build-guide
* Code: https://github.com/smagoun/simpsonstv
* Reddit thread w/ notes/questions: https://www.reddit.com/r/3Dprinting/comments/pdan45/im_the_maker_of_the_desktop_simpsons_tv_and_im/
* Another reddit thread: https://www.reddit.com/r/RASPBERRY_PI_PROJECTS/comments/q22sly/simpsons_tv_another_display_connection_help/
* TinyTV (similar project): https://github.com/eat-sleep-code/tiny-tv
* Waveshare docs (including pinout): https://www.waveshare.com/wiki/2.8inch_DPI_LCD

# streamstick
Turn your raspberry pi zero (or any pi) into a stream receiver.  VLC or OSB studio can be used to create a local stream that any other computer on your network can tap into.  This application will utilize the raspberry pi zero as a 'media stick' that you can plug into other TVs or devices and upon boot, will start playing the stream URL you set.

## Setup
Download the latest raspberry pi image for your application.  I will not do the step-by-step here.  You will want to insure SSH is enabled and you are able to connect to a wifi access point as well. Also, make sure to do a fresh update as well.

1. Lets install 'unclutter'
```sudo apt-get install unclutter```

2. This next step is only needed if you want to change the rotation and framebuffer (depending on your display).  Here we're going to edit the display boot config.
```sudo nano /boot/config.txt```
Add in the following lines (you would set rotation as desired).
```# Display orientation. Landscape = 0, Portrait = 1
display_rotate=1

# Use 24 bit colors
framebuffer_depth=24```

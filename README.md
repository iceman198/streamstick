# streamstick
Turn your raspberry pi zero (or any pi) into a stream receiver.  [VLC](https://www.videolan.org/vlc/) or [OSB Studio](https://obsproject.com/) can be used to create a local stream that any other computer on your network can tap into.  This application will utilize the raspberry pi zero as a 'media stick' that you can plug into other TVs or devices and upon boot, will start playing the stream URL you set.

## Setup
Download the latest raspberry pi image for your application.  I will not do the step-by-step here.  You will want to insure SSH is enabled and you are able to connect to a wifi access point as well. Also, make sure to do a fresh update as well.

1. Lets install chromium: `sudo apt-get install chromium-browser`

2. Create a new directory for our code: `mkdir ~/streamstick`

3. Go into our new directory: `cd ~/streamstick`

4. Download the streaming page: `wget https://github.com/iceman198/streamstick/src/index.html`

5. Lets install 'unclutter': `sudo apt-get install unclutter`

6. This next step is only needed if you want to change the rotation and framebuffer (depending on your display).  Here we're going to edit the display boot config. Open it up in the editor: `sudo nano /boot/config.txt` and add in the following lines (you would set rotation as desired).
```
# Display orientation. Landscape = 0, Portrait = 1
display_rotate=1

# Use 24 bit colors
framebuffer_depth=24
```

7. Now lets get things to autostart. Lets make a backup of our current one using `sudo mv ~/.config/lxsession/LXDE-pi/autostart ~/.config/lxsession/LXDE-pi/autostart_backup` and then we can create a new one using `sudo nano ~/.config/lxsession/LXDE-pi/autostart`.  Paste in the following.
```
@xset s off
@xset -dpms
@xset s noblank
@chromium-browser --noerrdialogs --incognito --kiosk ~/streamstick/index.html
```


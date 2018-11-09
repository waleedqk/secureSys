# Main Hub

**Enable ssh**

navigate to the boot folder in the SD card

    touch ssh

**WiFi Credentials**

navigate to the boot folder in the SD card

    vim wpa_supplicant.conf

add the following lines of code

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
ssid="ENG404"
psk="Pakistan123"
scan_ssid=1
}
```

**Search for all Pi's on the network**

    arp -na | grep -i b8:27:eb 

Or log into the router: http://192.168.0.1/l

    cusadmin


**SSH into the pi**

Power up the pi for the first time and wait for a bit:

    ssh pi@raspberrypi.local

**Expand Filesystem**

    sudo raspi-config

**Change the Password**

    sudo passwd pi

**Update the Pi**

    sudo apt-get update && sudo apt-get upgrade -y

**Change the Hostname**

    Follow the instructions in the hostname.md file

**ssh keys**

Copy over ssh keys to to enable passwordless entry into the pi. Follow the instructions in passwordless_ssh.md.

**Install Dependencies**

Run the ```sudo bash scripts/hub/hub_install.bash -n``` script on the pi.

# 5" Display Kippah Portable Raspberry Pi

**Guide from**

    https://learn.adafruit.com/portable-kippah-pi?view=all

for the display

    https://www.adafruit.com/product/1680

5.0" 40-pin 800x480 TFT Display without Touchscreen

**Update & Upgrade**

    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install rpi-update
    sudo rpi-update
    sudo reboot

**Install and Try raspi-gpio**

    sudo apt-get install raspi-gpio
    sudo raspi-gpio get

**Install Device Tree Blob**

    cd ~
    wget https://raw.githubusercontent.com/adafruit/Adafruit-DPI-Kippah/master/dt-blob.bin
    sudo cp dt-blob.bin /boot/

**Update configuration**

    sudo vim /boot/config.txt

and add the following lines at the bottom

    # Disable spi and i2c, we need these pins.
    dtparam=spi=off
    dtparam=i2c_arm=off

    # Set screen size and any overscan required
    overscan_left=0
    overscan_right=0
    overscan_top=0
    overscan_bottom=0
    framebuffer_width=800
    framebuffer_height=480

    # enable the DPI display
    enable_dpi_lcd=1
    display_default_lcd=1

    # set up the size to 800x480
    dpi_group=2
    dpi_mode=87

    # set up the hsync/vsync/clock polarity and format
    dpi_output_format=454661

    # set up the size to 800x480
    hdmi_timings=800 0 40 48 88 480 0 13 3 32 0 0 0 60 0 32000000 6

**Change Display setting**

This sets up the screen, if you ever want to temporarily 'undo the DPI Hat install' just delete these lines under: `sudo vim /boot/config.txt` and reboot

    enable_dpi_lcd=1
    display_default_lcd=1

# Test Display Installation 

**Test Video**

    cd ~/Videos
    wget http://adafruit-download.s3.amazonaws.com/bigbuckbunny320p.mp4
    omxplayer bigbuckbunny320p.mp4

or alternatively

    omxplayer /opt/vc/src/hello_pi/hello_video/test.h264
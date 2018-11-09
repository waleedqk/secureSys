# Camera

## Flash the OS

Download image from the official GitHub releases page:

    https://github.com/ccrisan/motioneyeos/releases

and flash it on the SD card.

**Enable ssh**

navigate to the boot folder in the SD card

    touch ssh

SSH is enabled by default and you should use the “admin” user account with the password you set in the settings. If you haven’t changed the default password it will be blank but I recommend you set a decent password and don’t leave it on the default.

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

## Power On

Power on the pi and once it connects to the internet let it finsih its first boot sequence for a while.

## View the Feed

To view the feed from the camera, figure out the IP address alotted to it and then enter it into the address bar of your browser.

## Default Login

    user: admin
    pass: <blank>

# Settings

## Account Setup

Under general settings you should set passwords for “Admin Password” and “Surveillance Password”.

## Change Camera Name

Under ```Video Device``` change the “Camera Name” to a unique value: kamraPi

## Advanced Settings

Under the advacned settings tab change the hostname and the time zone for the pi.

## Fixed IP Address

To make it easier to find the web interface in the future I like to give my cameras a fixed IP address. The IP address can be specified in the Network settings.

## Rotation / Orientation

If your camera is mounted upside-down you can use the Video Rotation setting to rotate the image.

## Preferences

    Enable CSI Camera Led = OFF
    Overclocking = PiZero

## Repository

https://github.com/ccrisan/motioneyeos/wiki

## References

https://www.raspberrypi-spy.co.uk/tag/motioneyeos/

https://www.raspberrypi-spy.co.uk/2017/04/raspberry-pi-zero-w-cctv-camera-with-motioneyeos/

https://www.raspberrypi-spy.co.uk/2017/08/send-pushover-notification-when-motioneyeos-boots/

https://thepihut.com/blogs/raspberry-pi-tutorials/34708676-starting-something-on-boot
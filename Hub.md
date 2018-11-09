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
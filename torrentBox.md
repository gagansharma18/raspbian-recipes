# INSTALL 
```
$ sudo apt-get update && sudo apt-get install transmission-daemon
```
```
$ sudo service transmission-daemon stop
```
```
$ sudo nano /etc/transmission-daemon/settings.json
```
```
# Transmission-daemon configuration file #
{
    "alt-speed-down": 50,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 50,
    "bind-address-ipv4": "0.0.0.0",
    "bind-address-ipv6": "::",
    "blocklist-enabled": false,
    "blocklist-url": "http://www.example.com/blocklist",
    "cache-size-mb": 4,
    "dht-enabled": true,
    "download-dir": "/media/pi/GBOX_DRIVE/Torrent_complete",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "download-queue-enabled": true,
    "download-queue-size": 5,
    "encryption": 0,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/media/pi/GBOX_DRIVE/Torrent_inprogress",
    "incomplete-dir-enabled": true,
    "lpd-enabled": false,
    "max-peers-global": 200,
    "message-level": 1,
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 200,
    "peer-limit-per-torrent": 50,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": false,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": false,
    "preallocation": 1,
    "prefetch-enabled": true,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2,
    "ratio-limit-enabled": false,
    "rename-partial-files": true,
    "rpc-authentication-required": false,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-host-whitelist": "",
    "rpc-host-whitelist-enabled": true,
    "rpc-password": "{6700081cd4a04f8f68b97f8222af4a6c815ad723sdBLllXS",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "pi",
    "rpc-whitelist": "127.0.0.1,192.168.*.*",
    "rpc-whitelist-enabled": false,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "speed-limit-down": 100,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 100,
    "speed-limit-up-enabled": false,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 2,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": true
}
```

# CHANGE USER pi or root and accordingly change everywere same user
```
sudo nano /lib/systemd/system/transmission-daemon.service
```
```
User=root
```
```
systemctl daemon-reload
```
```
sudo nano transmission-daemon.service
```

# check errors
```
sudo service transmission-daemon start
Job for transmission-daemon.service failed because the control process exited with error code.
See "systemctl status transmission-daemon.service" and "journalctl -xe" for details.
```
```
top  // transmission-daemon shoud start with pi user

sudo chmod 644 /home/pi/.config/transmission-daemon/settings.json

```


```
sudo systemctl start transmission-daemon
```
```
sudo chown -R pi:pi /etc/transmission-daemon/settings.json
sudo chmod -R 644 /etc/transmission-daemon/settings.json
```

# give drive permission
```
sudo chown -R root:root /media/pi/GBOX_DRIVE/
sudo chmod -R a+rwx /media/pi/GBOX_DRIVE/
sudo chown -R pi:pi /etc/transmission-daemon
sudo chmod 644 /var/lib/transmission-daemon/.config/transmission-daemon/settings.json
```
## SMB
```
sudo apt-get install samba samba-common-bin
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.old
sudo nano /etc/samba/smb.conf
```
## add at very bottom
```
[TORRENTS]
comment = Torrents
path = /mnt/usbdrive
create mask = 0755
directory mask = 0755
read only = no
browseable = yes
public = yes
force user = pi
only guest =no
```
# get UUID of HDD
```
sudo blkid
```
 LABEL="GBOX_DRIVE" UUID="39d8e281-ccc7-444c-aa01-522d1d63875b" 


# Add entry in fs tab
```
sudo nano /etc/fstab
```
```
proc            /proc           proc    defaults          0       0
PARTUUID=bd042b1b-01  /boot           vfat    defaults          0       2
PARTUUID=bd042b1b-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
UUID=39d8e281-ccc7-444c-aa01-522d1d63875b /mnt/usbdrive auto defaults,user,nofail 0 1
#UUID=39d8e281-ccc7-444c-aa01-522d1d63875b /mnt/usbdrive ext4 defaults,user,nofail,noatime 0 1
```
# add read write and execute permissin to torrent folder
```
sudo chown -R debian-transmission:debian-transmission /mnt/usbdrive/
sudo chmod -R a+rwx /mnt/usbdrive/
```

# Add path in network(Windows)
```
\\gbox\Torrents
```

# MOUNT A DRIVE 
UUID=39d8e281-ccc7-444c-aa01-522d1d63875b /media/pi/GBOX_DRIVE auto defaults,user,nofail 0 1


# Installation steps of usbmount BEST SOLUTION:

1. Install the package:
```
sudo apt-get install usbmount
```
2. Make sure it works in Stretch by changing MountFlags=slave to MountFlags=shared here:
```
sudo nano /lib/systemd/system/systemd-udevd.service
```
3. Reboot and it works! check the mount location by
```
df
```


# RPI 4 USB3 speed issue fix
```
1. Finding the VID and PID of your USB SSD
Disconnect the USB SSD. In a terminal window, run the command sudo dmesg -C.
Now, plug in the SSD and run dmesg with no parameters.
You should get output that looks like this:
Code: Select all

[ 4096.609817] usb 2-1: new SuperSpeed Gen 1 USB device number 4 using xhci_hcd
[ 4096.646369] usb 2-1: New USB device found, idVendor=2109, idProduct=0715, bcdDevice=a0.00
[ 4096.646385] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4096.646397] usb 2-1: Product: SABRENT
[ 4096.646409] usb 2-1: Manufacturer: SABRENT
[ 4096.646421] usb 2-1: SerialNumber: 000000123AD2
[ 4096.655154] scsi host0: uas
[ 4096.669178] scsi 0:0:0:0: Direct-Access              SABRENT          2210 PQ: 0 ANSI: 6
[ 4096.670993] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 4096.673710] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/112 GiB)
The idVendor and idProduct are the two hexadecimal numbers you need to take a note of.

1a. Multiple SSDs
If you have multiple USB SSD devices plugged into a single Pi 4, then for each device experiencing issues repeat Step 1 above and make a note of each idVendor and idProduct pair.

2. Add the quirks to /boot/cmdline.txt
Run a text editor as root - sudo nano /boot/cmdline.txt from the console or sudo leafpad /boot/cmdline.txt from the desktop.
At the start of the line of parameters, add the text usb-storage.quirks=aaaa:bbbb:u where aaaa is the idVendor for your device and bbbb is the idProduct. So, with the device above the string will be usb-storage.quirks=2109:0715:u.
cmdline.png
cmdline.png (21.45 KiB) Viewed 10602 times
For multiple devices with different VID:PID pairs, expand the parameter with a comma between each vid:pid:u triplet like this: usb-storage.quirks=0123:4567:u,2109:0715:u.

Save the file and exit the editor.

3. Reboot.

4. Check that it worked
To check that the quirk has been applied successfully, run dmesg | grep usb-storage and check that the VID and PID is listed as having a quirk applied:
Code: Select all

[    2.495725] usb 2-1: UAS is blacklisted for this device, using usb-storage instead
[    2.512739] usb 2-1: UAS is blacklisted for this device, using usb-storage instead
[    2.531823] usb-storage 2-1:1.0: USB Mass Storage device detected
[    2.549642] usb-storage 2-1:1.0: Quirks match for vid 2109 pid 0715: 800000
[    2.566177] scsi host0: usb-storage 2-1:1.0
Typically, most drives are still performant with usb-storage. They may not be able to saturate a USB3.0 connection but should still get 150-200MB/s under most workloads.
```

# AUTOMOUNT FIX WITH CONSOLE RPI4
```
/lib/systemd/system/systemd-udevd.service

Before: PrivateMounts=yes

After: PrivateMounts=no

Then I rebooted and it was OK ;)
```
Note: If running Desktop headless:
Use sudo raspi-config to set a screen resolution to something other than default.

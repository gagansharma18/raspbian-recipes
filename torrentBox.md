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

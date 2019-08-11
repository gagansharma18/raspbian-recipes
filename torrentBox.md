```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install transmission-daemon
sudo nano /etc/transmission-daemon/settings.json
```
## change download and incomplete directories
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

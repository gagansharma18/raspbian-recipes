
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install transmission-daemon
sudo nano /etc/transmission-daemon/settings.json
## change download and incomplete directories

sudo apt-get install samba samba-common-bin
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.old
sudo nano /etc/samba/smb.conf
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
sudo blkid
 LABEL="GBOX_DRIVE" UUID="39d8e281-ccc7-444c-aa01-522d1d63875b" 


# Add entry in fs tab
sudo nano /etc/fstab

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
94  sudo chmod -R a+rwx /mnt/usbdrive/


    1  sudo raspi-config
    2  restart
    3  exit
    4  sudo shutdown -w now
    5  sudo shutdown -h now
    6  ifconfig
    7  sudo apt-get update
    8  sudo apt-get upgrade
    9  sudo apt-get install transmission-daemon
   10  sudo apt-get install ntfs-3g
   11  sudo reboot
   12  sudo nano /etc/transmission-daemon/settings.json
   13  flist -l
   14  sudo fdisk -l
   15  ls /dev/sda2
   16  ls
   17  dir
   18  /dev/sda2
   19  cd /dev/sda2
   20  cd pi
   21  ls
   22  sudo mkdir /mnt/usbdrive
   23  sudo mount /dev/sda2 /mnt/usbdrive
   24  ls /mnt/usbdrive
   25  sudo nano /etc/transmission-daemon/settings.json
   26  sudo service transmission-daemon reload
   27  sudo service transmission-daemon stop
   28  ls -l
   29  sudo nano /etc/init.d/transmission-daemon
   30  sudo mkdir -p /home/username/.config/transmission-daemon/
   31  sudo ln -s /etc/transmission-daemon/settings.json /home/username/.config/transmission-daemon/
   32  ls -l
   33  ls
   34  sudo nano /etc/init.d/transmission-daemon
   35  ls -l /mnt/usbdrive
   36  sudo nano /etc/init.d/transmission-daemon
   37  sudo chown -R gagan:gagan /etc/transmission-daemon
   38  sudo nano /etc/init.d/transmission-daemon
   39  ifconfig
   40  sudo nano /etc/transmission-daemon/settings.json
   41  sudo service transmission-daemon reload
   42  sudo service transmission-daemon stop
   43  sudo service tranmission-daemon start
   44  sudo service transmission-daemon start
   45  sudo apt-get install openvpn -y
   46  ls -l /mnt/usbdrive
   47  sudo chwon -R pi:pi /mnt/usbdrive/
   48  sudo chown -R pi:pi /mnt/usbdrive/
   49  ls -l /mnt/usbdrive
   50  ls -l /mnt/
   51  sudo chown -R pi:pi /mnt/usbdrive/
   52  ls -l /mnt/
   53  ls -l /mnt/usbdrive
   54  cd /mnt/usbdrive
   55  ls
   56  touch a
   57  ls
   58  ls -l
   59  sudo chown -R pi:pi /mnt/usbdrive/
   60  chown -R pi:pi /mnt/usbdrive/
   61  ls -l
   62  cd ..
   63  ls -l
   64  cd ..
   65  ls -l
   66  cd mnt/usbdrive/
   67  ls
   68  cd Torrent_complete/
   69  ls
   70  cd ..
   71  cd Torrent_inprogress/
   72  ls
   73  ls -
   74  ls -l
   75  sudo nano /etc/transmission-daemon/settings.json
   76  ls -l
   77  ls
   78  sudo nano /etc/transmission-daemon/settings.json
   79  ls
   80  cd ..
   81  ls
   82  cd Torrent_complete/
   83  ls
   84  cd ..
   85  ls
   86  cd tmp/
   87  ls
   88  cd ..
   89  la
   90  ls
   91  cd mnt/usbdrive/
   92  cd Torrent_complete/
   93  ls
   94  cd ..
   95  cd usbdrive/
   96  ls
   97  cd Torrent_inprogress/
   98  ls
   99  sudo reboot
  100  ls
  101  cd mnt/usbdrive/
  102  fdisk -l
  103  sudo fdisk -l
  104  cd mnt/usbdrive/.
  105  cd mnt/usbdrive/
  106  cd /
  107  ls
  108  cd mnt/
  109  ls
  110  cd usbdrive/
  111  ls
  112  sudo nano /etc/samba/smb.conf
  113  sudo apt install samba samba-common-bin -y
  114  sudo blkid
  115  sudo nano /etc/fstab
  116  fdisk -l
  117  sudo fdisk -l
  118  df
  119  sudo mount /dev/sda1 /mnt/usbdrive
  120  cd ..
  121  sudo mount /dev/sda1 /mnt/usbdrive
  122  sudo fdisk -l
  123  sudo mount /dev/sda2 /mnt/usbdrive
  124  sudo mount -l
  125  df -h
  126  df
  127  sudo blkid
  128  sudo nano /etc/fstab
  129  man fstab
  130  sudo nano /etc/fstab
  131  sudo reboot
  132  ls
  133  sudo fdisk -l
  134  dh
  135  df
  136  ls /mnt/usbdrive/
  137  ls
  138  cd Torrent_inprogress
  139  cd /mnt/usbdrive/
  140  cd Torrent_inprogress/
  141  ls
  142  sudo reboot
  143  sudo raspi-config
  144  ls
  145  cd /mnt/usbdrive/
  146  ld
  147  ls
  148  cd Torrent_inprogress/
  149  ls
  150  sudo apt-get update
  151  sudo apt-get install connectd
  152  sudo apt-get update
  153  sudo apt-get install connectd
  154  sudo connectd_installer
  155  ls
  156  top
  157  la /mnt/usbdrive
  158  ls /mnt/usbdrive
  159  ls
  160  cd /mnt/usbdrive
  161  ls
  162  cd Torrent_inprogress/\[128gb\]-Omega.Retropie-DZ/
  163  ls
  164  sudo shutdown -h now
  165  dh
  166  dds
  167  ds
  168  df
  169  ls /mnt/usbdrive
  170  cd Torrent_inprogress
  171  ls
  172  raspi-config
  173  sudp raspi-config
  174  sudo raspi-config
  175  sudo shutdown -h now
  176  sudo fdisk -l
  177  sudo nano /etc/fstab
  178  df -h
  179  sudo fdisk -l
  180  sudo nano /etc/fstab
  181  sudo fdisk -l
  182  dh
  183  df -h
  184  sudo fdisk -l
  185  sudo nano /etc/fstab
  186  sudo raspi-config
  187  sudo nano /etc/fstab
  188  sudo shutdown -h now
  189  sudo blkid
  190  sudo nano /etc/fstab
  191  sudo blkid
  192  sudo nano /etc/fstab
  193  sudo reboot
  194  ls /mnt/usbdrive
  195  sudo fdisk -l
  196  df -h
  197  sudo nano /etc/fstab
  198  sudo reboot
  199  ls /mnt/usbdrive
  200  sudo shutdown -h now
  201  ps -A
  202  free -h
  203  w
  204  uptime
  205  raspi-config
  206  sudo raspi-config
  207  sudo shutdown -h now
  208  sudo connectd_installer
  209  sudo shutdown -h now
  210  ls
  211  sudo shutdown -h now
  212  sudo apt install speedtest-cli -y
  213  speedtest-cli
  214  sudo raspi-config
  215  sudo reboot
  216  sudo shutdown -h now
  217  sudo reboot
  218  sudo fdisk -l
  219  sudo nano /etc/fstab
  220  sudo service transmission-daemon stop
  221  sudo fdisk -l
  222  sudo unmount /dev/sda1
  223  sudo umount /dev/sda1
  224  sudo umount /dev/sda2
  225  sudo fdisk -l
  226  dh
  227  df
  228  fdisk -l
  229  sudo fdisk -l
  230  sudo fdisk /dev/sda
  231  sudo reboot
  232  fdisk -l
  233  sudo fdisk /dev/sda
  234  df
  235  sudo blkid
  236  sudo mkfs.ext4 /dev/sda1 -L GBOX_DRIVE
  237  sudo blkid
  238  fdisk -l
  239  sudo fdisk -l
  240  df
  241  sudo reboot
  242  df
  243  sudo fdisk -l
  244  sudo blkid
  245  sudo nano /etc/fstab
  246  sudo reboot
  247  df
  248  ls /mnt/usbdrive/
  249  sudo nano /etc/transmission-daemon/settings.json
  250  cd /mnt/usbdrive/
  251  ls
  252  mkdir Torrent_complete
  253  sudo chown -R pi:pi /mnt/usbdrive/
  254  mkdir Torrent_complete
  255  ls
  256  sudo nano /etc/transmission-daemon/settings.json
  257  mkdir Torrent_inprogress
  258  ls
  259  cd..
  260  cd ..
  261  df
  262  cd /mnt/usbdrive/
  263  ls
  264  cd /mnt/usbdrive/
  265  ls
  266  df
  267  sudo reboot
  268  cd /mnt/usbdrive/
  269  ls
  270  sudo chown -R pi:pi /etc/transmission-daemon
  271  ls -l
  272  sudo nano /etc/init.d/transmission-daemon
  273  sudo chown -R pi:pi /mnt/usbdrive/
  274  ls
  275  sudo service transmission-daemon stop
  276  sudo service transmission-daemon start
  277  sudo apt-get autoremove ntfs-3g
  278  sudo service transmission-daemon start
  279  sudo apt update
  280  sudo apt-get upgrade
  281  ls ~/.bash_history
  282  ls
  283  ls ~/.bash_history
  284  history
  285  sudo apt-get install transmission-daemon
  286  sudo apt-get autoremove transmission-daemon -y
  287  sudo apt-get install transmission-daemon -y
  288  sudo nano /etc/transmission-daemon/settings.json
  289  sudo shutdown -h now
  290  cd /mnt/usbdrive/
  291  ls
  292  sudo shutdown -h now
  293  cd /mnt/usbdrive/
  294  ls
  295  df
  296  sudo reboot
  297  sudo chown -R debian-transmission:debian-transmission /mnt/usbdrive/
  298  sudo chown -R pi:pi /mnt/usbdrive/
  299  sudo nano /etc/init.d/transmission-daemon
  300  sudo service transmission-daemon stop
  301  sudo service transmission-daemon start
  302  top
  303  sudo chown -R pi:pi /etc/transmission-daemon
  304  sudo service transmission-daemon stop
  305  sudo chown -R pi:pi /etc/transmission-daemon
  306  sudo service transmission-daemon start
  307  systemctl status transmission-daemon.service
  308  sudo service transmission-daemon start
  309  top
  310  which transmission-daemon
  311  cd /usr/bin/
  312  ls
  313  ls -l
  314  sudo nano /etc/init.d/transmission-daemon
  315  sudo reboot
  316  ufw
  317  top
  318  sudo raspi-config
  319  top
  320  sudo nano /etc/init.d/transmission-daemon
  321  sudo chown -R debian-transmission:debian-transmission /mnt/usbdrive/
  322  transmission-show
  323  transmission-cli
  324  top
  325  sudo raspi-config
  326  lscpu
  327  top
  328  sudo raspi-config
  329  top
  330  sudo shutdown -h now
  331  sudo nano /etc/init.d/transmission-daemon
  332  sudo chown -R g+w /mnt/usbdrive/
  333  sudo chmod -R g+w /mnt/usbdrive/
  334  ls
  335  cd /mnt/
  336  ls
  337  ls -l
  338  su
  339  cd usbdrive/
  340  ls
  341  cd Torrent_complete/
  342  ls
  343  sudo rm -R "Bad Times At The El Royale 2018 1080p BluRay x264 Dual Audio [Hindi DD 5.1 - English DD 5.1] ESub [MW]"/
  344  ls
  345  sudo rm -R Batman.vs.Teenage.Mutant.Ninja.Turtles.2019.1080p.WEB-DL.DD5.1.H264-CMRG\[EtHD\]/
  346  sudo rm -R xXx
  347  sudo rm -R xXx\ Trilogy\ 2002-2017\ BluRay\ Dual\ Audio\ \[Hindi\ 5.1\ +\ English\ 5.1\]\ 720p\ x264\ AAC\ ESub\ -\ mkvCinemas\ \[Telly\]/
  348  ls
  349  dh
  350  df
  351  ls
  352  sudo shutdown -h now
  353  sudo shutdown -h now
  354  df
  355  sudo fdisk -l
  356  sudo shutdown -h now
  357  sudo fdisk -l
  358  df -h
  359  sudo fdisk -l
  360  sudo blkid
  361  sudo nano /etc/fstab
  362  df -h
  363  sudo mount -l
  364  histpry
  365  history
  366  sudo mount /dev/sda2 /mnt/usbdrive
  367  sudo blkid
  368  sudo mount /dev/sda1 /mnt/usbdrive
  369  sudo nano /etc/fstab
  370  df -l
  371  sudo blkid
  372  sudo nano /etc/fstab
  373  sudo reboot
  374  sudo nano /etc/fstab
  375  sudo blkid
  376  sudo reboot
  377  sudo chmod -R g+w /mnt/usbdrive/
  378  sudo chmod -R r+w /mnt/usbdrive/
  379  sudo chmod -R 666 /mnt/usbdrive/
  380  sudo chmod -R a+rw /mnt/usbdrive/
  381  sudp raspi-config
  382  sudo raspi-config
  383  history
  384  cd /mnt/usbdrive/
  385  sudo chown -R debian-transmission:debian-transmission /mnt/usbdrive/
  386  cd /mnt/usbdrive/
  387  cd /mnt/
  388  ls
  389  ls -l
  390  cd usbdrive/
  391  sudo chmod -R a+rw /mnt/usbdrive/
  392  ls
  393  ls -l
  394  sudo chmod -R a+rwx /mnt/usbdrive/
  395  ls -l
  396  cd usbdrive/
  397  ls
  398  sudo raspi-config
  399  sudo apt-get upgrade
  400  sudo reboot
  401  sudo shutdown -h now
  402  sudo raspi-config
  403  ls
  404  sudo reboot
  405  sudo apt-get update
  406  sudo raspi-config
  407  sudo shutdown -h now
  408  history
  409  1  sudo raspi-config
  410  history
pi@gbox:~ $

```
I think with these instructions, this issue can be closed:

I set my hostname to picam after installation and changing the default password.
This is how I then installed Motioneye on a Pi2 with Raspbian-Stretch (2017-09-07):

// steps on PiZeroW, Pi2:
sudo apt-get update
sudo apt-get dist-upgrade
//
sudo nano /etc/modules
// add:
bcm2835-v4l2
//
//
// extra packages:
sudo apt-get install libssl-dev libcurl4-openssl-dev libmariadbclient18 libpq5 mysql-common ffmpeg
//
// prebuilt motion deb package:
wget https://github.com/Motion-Project/motion/releases/download/release-4.0.1/pi_stretch_motion_4.0.1-1_armhf.deb
sudo dpkg -i pi_stretch_motion_4.0.1-1_armhf.deb
//
// install motioneye:
sudo pip install motioneye
//
// setup to run motioneye:
sudo mkdir -p /etc/motioneye
sudo cp /usr/local/share/motioneye/extra/motioneye.conf.sample /etc/motioneye/motioneye.conf
sudo mkdir -p /var/lib/motioneye
sudo cp /usr/local/share/motioneye/extra/motioneye.systemd-unit-local /etc/systemd/system/motioneye.service
sudo systemctl daemon-reload
sudo systemctl enable motioneye
sudo systemctl start motioneye
//
// To enable web control from local network, seems missing from the docs:
// edit both /etc/motioneye/motioneye.conf and /etc/motioneye/motion.conf and then reboot.
// In /etc/motioneye/motion.conf Change webcontrol_localhost on To webcontrol_localhost off
// In /etc/motioneye/motioneye.conf Change motion_control_localhost true To motion_control_localhost false
// then reboot system
// can pause and resume motion detection from a terminal or node-red etc. with commands:
curl http://picam:7999/1/detection/pause -s -o /dev/null
curl http://picam:7999/1/detection/start -s -o /dev/null
```

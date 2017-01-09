# xbian-package-a2dp
bluetooth a2dp audio for xbian

Goals:
- Stream bluetooth audio TO your Raspberry Pi 3. For example to be used in car.
- Automatically make it discoverable for your phone (iOS/Android), just like a bluetooth speaker
- No pairing from commandline required
- Everything should start automatically on boot
- External USB audio adapter reccomended for good quality


Not completely working yet!! WIP for Raspberry Pi 3 (b).

Install on your Raspberry (v3) with the following commands:

sudo apt-get install bluez alsa-base alsa-utils pulseaudio pulseaudio-module-bluetooth pulseaudio-utils python-gobject python-gobject-2 bluez-tools

sudo sh -c "echo 'extra-arguments = --exit-idle-time=-1 --log-target=syslog' >> /etc/pulse/client.conf"
sudo hciconfig hci0 up
sudo hciconfig hci0 class 0x200420
sudo reboot

sudo su -

apt-get update

apt-get install git fakeroot

cd /root
git init
git clone https://github.com/belese/xbian-package-a2dp
cd xbian-package-a2dp

./gen.package.sh

Now you should have a debian package called:
xbian-package-a2dp1.1.deb

Proceed to install it:

dpkg -i xbian-package-a2dp1.1.deb

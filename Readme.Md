# Guide to linux for ASUS ROG laptops
### I purchased my laptop last year and have been distro hopping on it for a while .
- Ive learned a lot of new things using linux and here's my wisdom
### first step 
-if u want to boot or install a linux distro on this laptop add "nouveau.modeset=0" in the grub files commands after "splash". This is alot necessary otherwise your system would hang up in between.
### three types of gpu profiles that u'll see in majority of the distros
- nvidia gpu(uses the nvidia gpu terrible battery life but necessary for games)
- intel gpu(good for daily use best for battery life)
- hybrid gpu(good for daily use but battery life is less than intel gpu and it heats up sometimes)a(it basically runs on intel and when the system feels nvidia gpu is neccessary it runs on that. nvidia gpu kinda keeps on running in the background and hoggs up battery)
#### The bests distros that work best without any additional settings
- Pop!_OS by System76 (use the nvidia iso to have no issues while setting it up. no heating issue)
- manjaro ( it lacks a switch to select gpu which will kinda result in bad battery life but ill be uploading an easy script for that)
#### The bests distros that work with additional changes
- linux mint(a good distro comes with a switchable graphics profile but heats up a bit kinda bad on battery too but we'll get to that later)
- deepin (bad on battery life but the most beautiful it comes with the hybrid gpu profile and u cant switch to intel only for battery life)
#### distros u should stay out of
- fedora kinda bad on battery life and uses hybrid graphics and u cant switch to intel gpu
- mx linux (no nvidia support for our laptop)
- kali or other security os( the 440 driver is kinda broken ull have alot more system crashes so u should stay out of them for a while)
## Customizing your linux for better battery and performance
### Thermald
- it kinda maintains your laptop temperature and tries to cool it down
#### for arch-linux or manjaro
```
pamac install thermald
sudo systemctl enable --now thermald
```
#### for debian or ubuntu based
```
sudo apt install thermald
sudo apt-get install -y thermald
```
### TLP
- the best tool to save battery life
- i have uploaded my own settings u can replace ur config with mine for best battery life
#### for arch-linux or manjaro
```
pamac install tlp
systemctl enable tlp --now
```
rename the config file to tlp and move it to /etc/tlp.conf
#### for debian or ubuntu based distro
```
apt install tlp tlp-rdw
sudo tlp start
```
rename the config file to tlp and move it to /etc/default/tlp
### Intel-undervolt
- This is a tricky thing to get working
- for i7 undervolt not more than 100mv or it may crash
- for i5 u can go upto 140mv but ill suggest u to start from 20mv and move up until it crashes
#### for arch-linux or manjaro
- open software centre
- enable AUR
- search for intel-undervolt and build it
#### for debian or ubuntu based distro
```
git clone https://github.com/kitsunyan/intel-undervolt.git
cd intel-undervolt/
./configure && make && make install
```
##### after installing open terminal
```
sudo intel-undervolt read                    #to read your present voltage settings
sudo nano /etc/intel-undervolt.conf          #to edit ur config replace 0 after cpu and gpu to make it look like in the screenshot below 
sudo intel-undervolt apply                   #to apply ur settings
```
![Intel-undervolt](https://i.imgur.com/FNbgBHB.jpg)
the values in the screenshot are safe for i5 variants on intel graphics
## Gpu switch for manjaro or arch
-will be updated soon
## rgb control
ive compiled rgb control in this repo : https://github.com/drunckj/rog-rgb-control
## Want to buy me a coffee: https://www.paypal.me/drunkcj

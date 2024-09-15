# LicheePi4A
<br>


Hello All!

I just received my Sipeed Licheee Pi 4a laptop. It comes with an old verion of Debian which I want to upgrade to 
Ubuntu 24.04. I'll be posting update and findings here.
<br>
<br>
Links to boot in to mode<br>
https://wiki.sipeed.com/hardware/en/lichee/th1520/lpi4a/4_burn_image.html
<br>
Ubuntu Image
<br>
http://cdimage.ubuntu.com/ubuntu-base/releases/22.04/release/
<br>
The platform's defconfig contains all of the Linux kconfig settings required to properly configure the kernel build (features, default system parameters, etc) for that platform.
<br>
<br>
# Update Aug 19th

<br>

So after totally messing up my laptop it not booting anymore I spent a lot of time trying flashing the system back via fastboot. It looks like flashing it via shell script did the trick. I have no idea what the difference is between that and flashing it manually. I'll upload the script and files here soon.
<br>

https://cdimage.ubuntu.com/releases/noble/release/ubuntu-24.04-live-server-riscv64.img.gz

# U-Boot
<br>
<br>

DIP switches set it to EMMC mode. Press the BOOT button on the board and connect lpi4a to the computer using a data cable. Then perform the following operations:

Optional

sudo fastboot flash ram ./firmware/u-boot-with-spl.bin
sudo fastboot reboot
sleep 10
sudo fastboot flash uboot ./firmware/u-boot-with-spl.bin 


For installation of drivers, refer to the Sipeed official Wiki.

Flash the system
Option 1: Flash the system to an SD card

You can use Belena Etcher or other software.
Option 2: Flash the system to EMMC
(1) Use the UMS (USB Mass Storage) feature of u-boot (experimental):

Interrupt the u-boot countdown by pressing `Ctrl^C` when counting down using the serial port to enter the u-boot command line, then enter the following command:

ums 0 mmc 0 pci 

The EMMC will be mapped as a USB Mass Storage device on the computer, and you can use Etcher or other software to flash it.
(2) After booting from the SD card, use the dd command to copy the Armbian image to the EMMC.
4. Support status

It is recommended to use the legacy version based on T-Head SDK.
5. For 16GB version

First, you need to flash 16GB u-boot.
Second, you need to change “th1520-lichee-pi-4a.dts” to “th1520-lichee-pi-4a-16gb.dts” in /boot/extlinux/extlinux.conf.

<br>

# Make sure you flash it properly
<br>


![desktop2](https://github.com/user-attachments/assets/ee8af285-b21d-43fd-8118-ef6123fbcb82)

<br>
<br>

![motherboard](https://github.com/user-attachments/assets/784c73ae-b4b3-4529-b4cf-e71c9f4525b4)
<br>
<br>
I finally got it booting the way it was when I got it. Here's my script.  <br>

#! /bin/sh
# Script to flash images via fastboot, edit image path first
#


sudo fastboot flash ram u-boot-with-spl-plastic16g.bin<br>
sudo fastboot reboot<br>
sleep 5<br>
sudo fastboot flash uboot u-boot-with-spl-plastic16g.bin<br>
sudo fastboot flash boot  boot-console-20240529_143041.ext4u<br>
sudo fastboot flash root root-console-20240601_180941.ext4<br>





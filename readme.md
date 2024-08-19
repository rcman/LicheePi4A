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
So after totally messing up my laptop it not booting anymore I spent a lot of time trying flashing the system back via fastboot. It looks like flashing it via shell script did the trick. I have no idea what the difference is between that and flashing it manually. I'll upload the script and files here soon.
<br>

# LineageOS 17.1 image for RaspberryPi:
#
#   https://konstakang.com/devices/rpi3/LineageOS17.1/
#
# From the website:
#   Important! This image includes parts that are licensed under non-commercial license
#   (Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International).
#   You may use this build freely in personal/educational/etc use.
#   Commercial use is not allowed with this build!


sudo apt install libguestfs-tools
unzip lineage-17.1-20201108-UNOFFICIAL-KonstaKANG-rpi3.zip
mkdir mnt
guestmount -a lineage-17.1-20201108-UNOFFICIAL-KonstaKANG-rpi3.img -m /dev/sda2 -m /dev/sda1:/boot -m /dev/sda3:/vendor mnt
cp -r patches/* mnt/
guestunmount mnt
mv lineage-17.1-20201108-UNOFFICIAL-KonstaKANG-rpi3.img lineage-17.1-20201108-UNOFFICIAL-KonstaKANG-cm3panel.img
sudo dd if=lineage-17.1-20201108-UNOFFICIAL-KonstaKANG-cm3panel.img of=/dev/sdXXX bs=4M status=progress

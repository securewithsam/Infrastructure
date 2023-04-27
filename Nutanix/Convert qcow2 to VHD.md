

Step One: Extract Disk Image from OVA
tar -xvf wfmqcow2.ova


Step Two: Convert Disk Image to QCOW2
sudo apt-get install qemu-utils

To check a list of all disk image formats supported by qemu-img
qemu-img -h | tail -n1


Step Three:Convert the QCOW2 image to a raw file format
qemu-img convert -f qcow2 -O raw 3a32b468-62fa-46ae-951e-99e13e6fa7fa.qcow2 3a32b468-62fa-46ae-951e-99e13e6fa7fa.raw


Step Four: 
qemu-img convert -f raw -o subformat=fixed -O vpc 3a32b468-62fa-46ae-951e-99e13e6fa7fa.raw 3a32b468-62fa-46ae-951e-99e13e6fa7fa.vhd

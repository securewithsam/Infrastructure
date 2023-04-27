
#### Export the VM to qcow2 in prism central 

```sh
Login to Prism
Select the VM > Actions > Export as OVA > Select QCOW2 > Save it on local disk .

WinSCP into any Linux VM 
Copy the above qcow2 file and follow the steps below 

```
```sh
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
```

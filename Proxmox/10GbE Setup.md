#### Setup Proxmox with 10GbE Network 

##### Connect te DAC /FC cable from the Server SFP+ port to the 10G Switch and create a new vmbr1 

![image](https://github.com/securewithsam/Virtualization/assets/85324643/3a6d82f6-f970-4c8d-b0a7-d4f6c3900a4d)


#### Go to PVE shell and add the line below to set MTU 

```sh
pre-up ip link set ens2f1np1 mtu 9000
```
![image](https://github.com/securewithsam/Virtualization/assets/85324643/ad50608b-f078-4568-88cc-33a8cb66fbdf)

#### reboot the server 

#### Crate a new VM and select the newly created vmbr1 
![image](https://github.com/securewithsam/Virtualization/assets/85324643/15c1d1cf-1d20-41a8-8f88-1bd435413146)

#### On the VM created , enable the jumbo packet and reboot the server 

![image](https://github.com/securewithsam/Virtualization/assets/85324643/6453596c-09a1-4c8a-86cf-17cd0025dec3)

![image](https://github.com/securewithsam/Virtualization/assets/85324643/9942e3eb-b898-407d-94b8-0fafa4d1eee2)


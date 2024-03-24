## Reshuffling  G7 nodes from Datacenter A to Datacenter B in a different cluster .

### Step 1: Mark node for removal in prism element

![image](https://github.com/securewithsam/Virtualization/assets/85324643/88dd0134-2ab0-40be-8c17-c13030cb4238)

### Step 2: 
Change the IPMI IP of the node to match the current DC subnet 
Restart the node and press Delete to enter the BIOS setup utility.
There is a limited amount of time to enter BIOS before the host completes the restart process
![image](https://github.com/securewithsam/Virtualization/assets/85324643/974abcb9-03a4-4c86-a7af-64c5c055bb26)

### Step 3:
Login to the IPMI and assign DNS and change Hostname and default admin password

![image](https://github.com/securewithsam/Virtualization/assets/85324643/ff94c1e1-7930-4442-a497-de563ce9dd0a)

### Step 4:
Login to the Nutanix Foundation VM to assign IP addresses to the AHV and CVM -http://localhost:8000

![image](https://github.com/securewithsam/Virtualization/assets/85324643/925a3d1d-109b-464a-be32-702499b2ee5e)

![image](https://github.com/securewithsam/Virtualization/assets/85324643/a74760b6-483e-4a14-8fce-6933e9f2b08a)

### Step 4.1 [Optional] Change the IP manually instead of using foundation VM 
```sh
sudo vi /etc/sysconfig/network-scripts/ifcfg-br0
```


### Step 5: Once the IPs are changed, make sure they are pingable and then SSH into the  AHV and verify the interfaces are up 
```sh
manage_ovs show_interfaces
manage_ovs show_uplinks
```
### 2 There should be 2 Bridges and 3 Bonds present in the networking 
![image](https://github.com/securewithsam/Virtualization/assets/85324643/9d9b3069-e9f5-4d87-a421-06b0f4e107c6)

### Step 6: Change the root & admin password as desired 
```sh
sudo passwd root
```
Step 6: Change Hostnames
```sh
hostnamectl set-hostname --pretty node1
hostnamectl set-hostname --transient node1
hostnamectl set-hostname --static node1
```
#### Optional 
```sh
sudo nano /etc/hostname
sudo nano /etc/hosts
```
#### Step 7 :
SSH into the CVM and repeat the same as above and change the Hostname and reboot . 

#### Step 8 :
```sh
virsh list --all
```
If the hostname is still same and did not update to the new, then add the node to the cluster and then login to CVM and change the hostname and reboot CVM 
```sh
 change_cvm_display_name --cvm_ip=CVM-IP --cvm_name=new-name
```

#### Expand Cluster 

![image](https://github.com/securewithsam/Virtualization/assets/85324643/541fb848-63c4-4600-91dc-86210eb3f28c)


![image](https://github.com/securewithsam/Virtualization/assets/85324643/bd951945-1bb8-48b3-b45b-4e10b86446ad)

### After expansion is completed ,the cluster will complain about Inconsistent virtual switch , SSH into AHV , delete and re add the vswitch .
```sh
acli net.list_virtual_switch
acli net.migrate_br_to_virtual_switch br0 vs_name=vs0
acli net.migrate_br_to_virtual_switch br2 vs_name=DMZ
acli net.list_virtual_switch
```
 





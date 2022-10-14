 Step 1:
 Mark the node for removal 
 
 Step 2:
 Install AOS using foundation vm ( Match the version)
 ```sh
 http://localhost:8000
 ```
 
 Step 3:
 Match the current network settings on the existing cluster
  ```sh
 manage_ovs show_uplinks
 ```
 Match the bridge and bond config before adding the node to the cluster
 Configure network /bond via CVM
  ```sh
 manage_ovs --bridge br0 --interfaces eth3,eth5 --bond_name br0-up --bond_mode balance-tcp --lacp_mode fast --lacp_fallback true update_uplinks
 ```
 Step 4:
 Create new bridge 1
 ssh into AHV (root@192.168.5.1)
  ```sh
 allssh manage_ovs show_uplinks
 ```
  ```sh
 ovs-vsctl add-br br1
 ```
  ```sh
 ovs-vsctl add-bond br1 br1-up eth0 eth1
 ```
 ```sh
 ovs-appctl bond/show
 ```
 exit

Step 5:
Login into CVM to match the bond config for newely created bridge br1
 ```sh
manage_ovs --bridge br1 --interfaces eth4 --bond_name eth4 --bond_mode active-backup update_uplinks
```
 ```sh
manage_ovs show_uplinks
```
Step 4:
Expand cluster 
 
 
 
 

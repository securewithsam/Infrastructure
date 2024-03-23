### Adding G7 nodes in a different cluster in a different DC

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

#### Step 4:
Login to the Nutanix Foundation VM to assign IP addresses to the AHV and CVM -http://localhost:8000
![image](https://github.com/securewithsam/Virtualization/assets/85324643/925a3d1d-109b-464a-be32-702499b2ee5e)

![image](https://github.com/securewithsam/Virtualization/assets/85324643/a74760b6-483e-4a14-8fce-6933e9f2b08a)

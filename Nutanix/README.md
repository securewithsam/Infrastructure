## Nutanix Cluster Components

#### Stargate- Data I/O manager
#### Cassandra- Key Role : Distributed metadata store
#### Curator- Manage and distribute task throughout the cluster
#### Zookeeper-Cluster configuration manager
#### Prism - User Interface and API management 



## Nutanix Abbreviations:

<br>HCI (hyperconverged infrastructure) <br>
<br>AHV - (Acropolis Hypervisor)<br>
<br>Acropolis OS(AOS)<br>
<br>CVM (Controller VM)<br>
<br>NCC (Nutanix Cluster Check)<br>
<br>LCM- (Life Cycle Manager)<br>
<br>AMF(app mobility fabric)<br>
<br>DSF (Distributed Storage Fabric)<br>
<br>AFS- Acropolis Files Services<br>
<br>ABS- Acropolis Block Services<br>
<br>OVS- Open vSwitch<br>
<br>ADS- Acropolis Dynamic Scheduling (Like DRS in vSphere)<br>
<br>EC - (Erasure coding)<br>
<br>SCMA- (Security Configuration Management Automation)<br>
<br>RPO- (Recovery Point Objective )<br>
<br>RTO- (Recovery Time Objective)<br>
<br>CALM- Cloud Automation LifeCycle Manager<br>
<br>Self Service Restore (SSR)<br>
<br>cross-hypervisor disaster recovery (CHDR)<br>


## Networking

Linux Bridge (Virbr0) is used for internal communication (Mgmt & Storage) traffic between CVM & AHV Host/Node
OVS bridge (br0) This bridge connects to the physical switch 
vnet0 - These are Tap ports used to connects VMs to the bridge 
br0-up - Bonded/NiC Teaming  to connecting to physical NIC 
VXLAN - Used for IP Address management


## Bond Modes:
Active-Backups : Traffic from all VMs is sent thru single NIC ,if that NIC fails, the 2nd NIC is active (bandwidth of single adapter is used )  NO CHANGES TO PHYSICAL SWITCH IS REQUIRED
Balance-SLB: Traffic can be sent via both NICs and full bandwidth is used ( NO CHANGES TO PHYSICAL SWITCH IS REQUIRED)
LACP with balance-tcp :  CHANGES TO PHYSICAL SWITCH IS REQUIRED

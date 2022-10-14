#### Stargate- Data I/O manager
#### Cassandra- Key Role : Distributed metadata store
#### Curator- Manage and distribute task throughout the cluster
#### Zookeeper-Cluster configuration manager
#### Prism - User Interface and API management 



## Nutanix Abbreviations:

HCI (hyperconverged infrastructure)
AHV - (Acropolis Hypervisor)
Acropolis OS(AOS)
CVM (Controller VM)
NCC (Nutanix Cluster Check)
LCM- (Life Cycle Manager)
AMF(app mobility fabric)
DSF (Distributed Storage Fabric)
AFS- Acropolis Files Services
ABS- Acropolis Block Services
OVS- Open vSwitch
ADS- Acropolis Dynamic Scheduling (Like DRS in vSphere)
EC - (Erasure coding)
SCMA- (Security Configuration Management Automation)
RPO- (Recovery Point Objective )
RTO- (Recovery Time Objective)
CALM- Cloud Automation LifeCycle Manager
Self Service Restore (SSR)
cross-hypervisor disaster recovery (CHDR)


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

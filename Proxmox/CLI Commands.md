## Proxmox CLI Commands


PVEVersion
```sh
pveversion
```
Listing All Virtual Machines
```sh
qm list
```
Creating a New Virtual Machine
```sh
qm create 100 --name Ubuntu-01 --memory 2048 --net0 virtio,bridge=vmbr0
```
List all LXC containers:
```sh
pct list
```
Start an LXC container
```sh
pct start <VMID>
```
Getting Node Information
```sh
pvesh get /nodes
```
Adding a New User
```sh
pveum useradd jdoe@pve --password myPassword --firstname John --lastname Doe
```
Adding a Node to the Cluster
```sh
pvecm add <node-IP>
```
Enabling the Firewall
```sh
pve-firewall enable
pve-firewall add rule --action accept --source 192.168.1.0/24 --dest any --proto tcp --dport 22
```
Adding a Storage Pool
```sh
pvesm add dir --storage local-backup --path /var/lib/vz/backup
```
List Storage
```sh
pvesm status
```


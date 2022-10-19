nutanix@cvm:~$ manage_ovs show_uplinks
nutanix@cvm:~$ manage_ovs show_interfaces
nutanix@cvm:~$ allssh manage_ovs show_interfaces

### Bring the interface down 
Login to AHV :
```sh
ethtool eth0
ifdown eth0
```


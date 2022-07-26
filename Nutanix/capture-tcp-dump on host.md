Login to CVM 
```sh
acli vm.get VM-NAME
```
copy the host uuid [generated from the above command]
SSH into to the host IP 
```sh
virsh list --all
```
virsh dumpxml 'enter uuid here' from the above command to know the tap interfaces or chk in prism 

```sh
tcpdump -i tap0 -w /tmp/somename01.pcap
```
to analyze the dump , winscp to the path above /tmp and download the file and use wireshark .


## To check vswitch logs 

Login to host
```sh
cd /var/log/openvswitch/
ls
```

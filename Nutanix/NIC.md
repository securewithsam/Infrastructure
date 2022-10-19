### Issue:  Interface down alert from Prism Element even after the nics are disabled intentionally 
[ In this example, eth0 and eth1 are supposed to be down ,however the PE sends alerts that the NICs are down even after acknowledging and resolving]

### Login into CVM 
```sh
allssh cat /home/nutanix/data/serviceability/check_cvm_health_job_state.json
```
Delete the interfaces  lines eth0 eth1
```sh
nano /home/nutanix/data/serviceability/check_cvm_health_job_state.json
```
```sh
ctrl 0
ctrl x
```

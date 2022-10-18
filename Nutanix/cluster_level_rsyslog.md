### Enable rSyslog for a specific cluster - needs to be done at CVM level .


Login to the any CVM within the cluster 

```sh
ncli
```
```sh
rsyslog-config set-status enable=false
```
```sh
rsyslog-config add-server name=Rapid7 relp-enabled={true} ip-address=10.145.190.80 port=5678 network-protocol={ udp }
```
```sh
rsyslog-config ls-servers
```
```sh
rsyslog-config add-module server-name=Rapid7 module-name=ACROPOLIS level=CRITICAL include-monitor-logs={ false }
```
```sh

rsyslog-config set-status enable=true
```

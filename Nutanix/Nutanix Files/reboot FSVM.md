```sh
Below is the procedure to reboot the FSVMs.

1) SSH to any FSVM via a CVM.

2) Run the below to confirm that all services are running on all FSVMs
cs | grep -v UP

Example:
nutanix@FSVM:~$ cs | grep -v UP
NVM: 10.x.x.x Up, ZeusLeader, Disabled Auto-upgrade
NVM: 10.x.x.x Up, Disabled Auto-upgrade
NVM: 10.x.x.x Up, Disabled Auto-upgrade

3) Run the below on any FSVM to confirm if the file server is not in HA. If the FSVM was power cycled, run the command multiple times as it could take a minute before recovering.
afs ha.minerva_check_ha_state

Example:
nutanix@FSVM:~$ afs ha.minerva_check_ha_state
03/18/2024 08:41:53 AFS cluster in HA state: False

Note: False = not in HA

4) Run the below on any FSVM to perform SMB health checks to confirm that all checks pass
afs smb.health_check

Example:
nutanix@FSVM:~$ afs smb.health_check
Cluster Health Status:
Primary Domain Status: PASSED
Kerberos Share Access: PASSED
NTLM Share Access: PASSED

Node: 10.24.135.133 Health Status:
Clock Skew (41 second(s)): PASSED
smbd status: PASSED
winbindd status: PASSED

Node: 10.24.135.132 Health Status:
Clock Skew (41 second(s)): PASSED
smbd status: PASSED
winbindd status: PASSED

Node: 10.24.135.131 Health Status:
Clock Skew (41 second(s)): PASSED
smbd status: PASSED
winbindd status: PASSED

5) From the Prism UI, Power Off one of the FSVMs.

6) From the Prism UI, Power On the FSVM that was powered off.

7) Repeat the above steps for the remaining FSVMs once powered on.

```

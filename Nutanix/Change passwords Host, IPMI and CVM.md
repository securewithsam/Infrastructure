[All commands needs to be performed from a CVM part of Nutanix cluster]

###### Source : https://portal.nutanix.com/page/documents/kbs/details?targetId=kA00e000000LKXcCAO&a=d141c43f3c83bfa5effbda061bfdb3583a5c88745618ed240c6767a016801404058155359bb6cc41%3E

##### Use the below command to change the local 'root' account password for all AHV hypervisors in the Nutanix cluster. This can run from any CVM in the cluster.

```sh
echo -e "CHANGING ALL AHV HOST ROOT PASSWORDS.\nPlease input new password: "; read -rs password1; echo "Confirm new password: "; read -rs password2; if [ "$password1" == "$password2" ]; then for host in $(hostips); do echo Host $host; echo $password1 | ssh root@$host "passwd --stdin root"; done; else echo "The passwords do not match"; fi
```

##### Use the below command to change the local 'admin' account password for all AHV hypervisors in the Nutanix cluster. This can run from any CVM in the cluster.

```sh
echo -e "CHANGING ALL AHV HOST ADMIN PASSWORDS.\nPlease input new password: "; read -rs password1; echo "Confirm new password: "; read -rs password2; if [ "$password1" == "$password2" ]; then for host in $(hostips); do echo Host $host; echo $password1 | ssh root@$host "passwd --stdin admin"; done; else echo "The passwords do not match"; fi
```

##### Use the below command to change the local 'nutanix' account password for all AHV hypervisors in the Nutanix cluster. This can run from any CVM in the cluster.

```sh
echo -e "CHANGING ALL AHV HOST NUTANIX PASSWORDS.\nPlease input new password: "; read -rs password1; echo "Confirm new password: "; read -rs password2; if [ "$password1" == "$password2" ]; then for host in $(hostips); do echo Host $host; echo $password1 | ssh root@$host "passwd --stdin nutanix"; done; else echo "The passwords do not match"; fi
```

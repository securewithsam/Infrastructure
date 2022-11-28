### Login to CVM to get FSVM IP Details
```sh
ncli fs ls
```
### ssh 10.xx.xx.41 (FSVM IP)
```sh
afs
```
```sh
share.owner_fsvm (Folder Name)
share.owner_fsvm IT
```
```sh
exit
```
### cd to the share path printed above from FSVM and not afs
```sh
10.xx.xx.43 FSVM:~$ cd /zroot/shares/459fb866-e688-4acc-b9d8-02df1c2a5250/:1a95c138-dc72-70bc-7b38-a1b67aaccdc8/487f20ba-fef2-4fe0-a48d-2ed68bfe687f
```
```sh
ls
```
### To delete folder
```sh
rm -rf Network_Operations/
```

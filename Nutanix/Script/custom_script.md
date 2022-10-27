## Custom script to provide all info at once 

```sh
clear; echo -e "\e[3J"; { ncli host ls | grep -e Address -e Block -e Maintenance; host_upgrade_status; nodetool -h 0 ring > ~/tmp/nodetool_output.txt; echo && cat ~/tmp/nodetool_output.txt; echo; echo $(tail -n +3 ~/tmp/nodetool_output.txt | wc -l)\/$(svmips | wc -w) nodes are in the ring;echo $(grep -c Up ~/tmp/nodetool_output.txt)\/$(svmips | wc -w) nodes are \'Up\'; echo $(grep -c Normal ~/tmp/nodetool_output.txt)\/$(svmips | wc -w) nodes are \'Normal\'; for i in $(svmips); do (grep -q $i ~/tmp/nodetool_output.txt || echo CVM $i missing from the ring.) ; done; echo && rm ~/tmp/nodetool_output.txt; cluster status 2>/dev/null | grep -Ev 'UP|^$'; ncli pd ls-snaps | grep Size | tr -d '(,' | awk '{SUM += $6} END { split( "K M G T P" , v ); s=0; if( SUM<1024) printf("\n%g %s",SUM, "byte(s)"); else {while( SUM>=1024 ){ SUM/=1024; s++ } printf("\n%.2f %s",SUM, v[s]"iB")} print(" used by snapshots\n")}';echo 'Print CVM /home usage for upgrades; Expecting less than 80% for / and 75% for /home'; allssh "df -h |grep /home |grep -v disks; df -h | grep -wF /; ls -larth /home/nutanix/software_downloads/foundation/foundation*.tar.gz"; echo '  '; echo 'Print Node: AOS version; NCC version; CVM time; Uptime; Foundation'; allssh 'stargate --version |grep version; ncc --version; date; uptime; cat foundation/foundation_version'; } | cat
```

### To Fetch CVM IPs, Load, Ring Status & Other detailed status
```sh
nodetool -h 0 ring > ~/tmp/nodetool_output.txt; echo && cat ~/tmp/nodetool_output.txt; echo; echo $(tail -n +3 ~/tmp/nodetool_output.txt | wc -l)\/$(svmips | wc -w) nodes are in the ring;echo $(grep -c Up ~/tmp/nodetool_output.txt)\/$(svmips | wc -w) nodes are \'Up\'; echo $(grep -c Normal ~/tmp/nodetool_output.txt)\/$(svmips | wc -w) nodes are \'Normal\'; for i in $(svmips); do (grep -q $i ~/tmp/nodetool_output.txt || echo CVM $i missing from the ring.) ; done; echo && rm ~/tmp/nodetool_output.txt
```



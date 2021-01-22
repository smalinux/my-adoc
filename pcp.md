# Hi title

Glossary
```
DSO (dynamic shared object)
```


## Checklist
- [DONE] [Quick start] https://pcp.io/docs/guide.html  
- [DONE] [Quick start] RedHat Ch 6  
- [Later] Complete all https://pcp.io/docs/    
-  
-  
-  
-  
-  

## The basic PCP commands are:
pminfo
pmie
pmieconf


```
# pmdate(1) - display an offset date
$ pmdate -7d %d%m%Y
$ ./src/pmdate/pmdate %Y

# pmrep(1) - performance metrics reporter
$ pmrep -i '.*firefox.*' :proc-io
$ pmrep -1gUJ 3 proc.hog.cpu
$ pmrep -i wlan0 -v network.interface.out

# pmchart(1) - strip chart tool for Performance Co-Pilot

# pmstat(1) - high-level system performance overview
$ pmstat

# pminfo(1) - display information about performance metrics
## Executing pminfo alone will show all available metrics, but there are over 2000 on my distribution.
$ pminfo --help
$ pminfo
$ pminfo | wc -l
## how many metrics are available in each categor
$ pminfo | cut -d'.' -f1 | sort  | uniq -c
## To view the information about a metric you can use -f (-h to specify a host):
$ pminfo -f disk.dev.total -h localhost
## To view details about a metric use the -T option with pminfo:
$

## Endtime
$ pmval -T +4sec kernel.uname.distro  # after 4sec
$ pmval -s 4 kernel.uname.distro  # terminate after getting 4 samples

## Monitor system metrics in a top-like window
$ ./src/pcp/atop/pcp-atop
..
..
.. etc: https://pcp.io/docs/guide.html
```
## [From redhat chaper 6](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/monitoring_and_managing_system_status_and_performance/monitoring-performance-with-performance-co-pilot_monitoring-and-managing-system-status-and-performance#tools-distributed-with-pcp_monitoring-performance-with-performance-co-pilot)
Google: MONITORING PERFORMANCE WITH PERFORMANCE CO-PILOT  
```
## Start spy on & save the record
$ 6.3. Deploying a minimal PCP setup (from redhat chaper 6)
$ pmlogconf & pmlogger

## tools to view archived data (from redhat chaper 6)
$ pmdumptext, pmrep, or pmlogsummary

## Display a short description of the xfs.write_bytes metric:
$ pminfo --oneline xfs.write_bytes
## Display a long description of the xfs.read_bytes metric:
$ pminfo --helptext xfs.read_bytes
## Obtain the current performance value of the xfs.read_bytes metric:
$ pminfo --fetch xfs.read_bytes
## 6.7.3. Resetting XFS performance metrics with pmstore
$ back to RedHat ch 6

```
## [From PCP Quick Ref](https://pcp.io/docs/guide.html)
```
## Display detailed information about a performance metric and its current values:
$ pminfo -dfmtT disk.partitions.read

## PMID
$ pminfo -m disk.partitions.read
$ pminfo -M disk.partitions.read

## Monitoring Processes using process name (ex: seq)
$ pmstore hotproc.control.config 'fname == "seq"'
$ seq 0 1000000000000000000000000000000000
$ pminfo -f hotproc | grep seq
# back to: Monitoring “Hot” Processes with Hotproc >> pcp quick guide


```

```
pmafm >> pmlogger 
```

## Get the exe file of any command
```
$ find ~/pcp-repo/ -name "pminfo"
```


## [Visualizing iostat and sar Data](https://pcp.io/docs/guide.html)
```
$ iostat -t -x 2 > iostat.out
$ iostat2pcp iostat.out iostat.pcp
$ pmchart -t 2sec -a iostat.pcp
```




## Keywards -Google
```
Postfix - 
```

---------------------------------------
### Your lovely places (as a PCP programmer)
```
/home/smalinux/pcp/src/pmdas
A simple command line monitor tool is /usr/share/pcp/demos/pmclient (C language).

1.3.4. Application and Agent Development >> pcp.readthedocs.io

All Ch 8 >> pcp.readthedocs.io

1.2.11. Product Extensibility >> pcp.readthedocs.io

pmapi(3) - for making new monitoring tools
pmda(3) - for making new PMDAs
libpcp - the core PCP library.
```

### Best way to start & stop pmcd
```
/etc/rc.d/init.d/pmcd start
/etc/rc.d/init.d/pmcd stop
/etc/rc.d/init.d/pmcd status
/etc/rc.d/init.d/pmcd restart
```
### Best way to manipulate PMDAs
`${PCP_PMDAS_DIR}` == `cat src/include/pcp.conf | grep PCP_PMDAS_DIR`
```
/var/lib/pcp/pmdas/cisco ./Install
/var/lib/pcp/pmdas/cisco ./Remove
pcp
```
### Getting env variables
for example `PCP_RC_DIR=`
```
cat src/include/pcp.conf | grep "PCP_RC_DIR="
```
### list all PMDAs & lib.. )
```
man pmda<Tab><Tab>
```

### Critical points
```
1.1.3. Unification of Performance Metric Domains >> pcp.readthedocs.io

```

### Config files
use `cat src/include/pcp.conf | grep "PCP_PMCDCONF_PATH"`
```
/etc/pcp/pmcd/pmcd.conf
/etc/pcp/pmcd/pmcd.options
```
Where is my `pcp.conf` ?! to reslove all env vars..
```
F "pcp.conf"
```

# Hi title



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

## Monitor system metrics in a top-like window
$ ./src/pcp/atop/pcp-atop
..
..
.. etc: https://pcp.io/docs/guide.html

```

## Get the exe file of any command
```
$ find ~/pcp-repo/ -name "pminfo"
```


## (Visualizing iostat and sar Data)[https://pcp.io/docs/guide.html]
```
$ iostat -t -x 2 > iostat.out
$ iostat2pcp iostat.out iostat.pcp
$ pmchart -t 2sec -a iostat.pcp
```




```
Performance Metrics Domain Agents (PMDAs)
a Performance Metrics Name Space (PMNS)
````

* pmwebd - not found  
====================  
https://www.redhat.com/en/blog/getting-started-using-performance-co-pilot-and-vector-browser-based-metric-visualizations




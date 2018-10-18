# Yarn Cals

## Spreadsheet Adjustment

Cluster Specifications
- Worker nodes: 10
- Worker vcores: 20
- Worker spindles: 12
- Worker RAM: 128 GB
- 16GiB RAM per node

Changes made to the spreadsheet:
- Changed memory reserved for the OS to 5% of total RAM. Since we have 128GB of RAM, 6.4GB for the OS seems enough.
- Application Master memory changed to 1GB
- Changed `mapreduce.map.memory.mb` to 2GB and `mapreduce.map.java.opts.max.heap` to 80% of that value (80% is the current best practice).
- Changed `mapreduce.reduce.memory.mb` to 4GB and `mapreduce.reduce.java.opts.max.heap` to 80% of that value (80% it is the current best practice).

## Step 2

The workload factor should be affected by the kind of workload expected for the cluster and the ration of vcores to spindles. Value `1` usually means the nodes are CPU bound and `4` means they are I/O bound.

# Yarn Cals

## Spreadsheet Adjustment

My cluster hardware is very limited:
- 5 nodes
- 4 vCores per node
- 16GiB RAM per node

Changes made to the spreadsheet:

- `1` vCore for the OS (was `2`): lowered because of cluster size
- `yarn.scheduler.maximum-allocation-vcores` set to `1` (was `4`): lowered because of cluster size, to allow more containers to be allocated and also because there is only one disk.


**Notes:**

Since I only have 4 vcores, counting with OS, NodeManager, Datanode and CM Agent, I already have all 4 vcores allocated. This configuration has a clear overcommit of vcores, so the spreadsheet shows 0 vcores available for containers. Since the `yarn.scheduler.maximum-allocation-mb` is equal to `yarn.nodemanager.resource.cpu-vcores * 1024` (being `1024` the minimum recommended memory in bytes for a container), the spreadsheet shows `0` as the value for `yarn.scheduler.maximum-allocation-mb`.


## Step 2

The workload factor should be affected by the kind of workload expected for the cluster and the ration of vcores to spindles. Value `1` means the cluster is CPU bound and `4` means it is more I/O bound.

Testing the values in the spreadsheet for an "example cluster" with much higher hardware specifications, we can see that the ration between vcores and spindles affects the number of maps/reduces.

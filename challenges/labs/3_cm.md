### Content of /user
```
[root@node02 ~]# hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - fullerton fullerton          0 2018-10-19 08:47 /user/fullerton
drwxrwxrwx   - mapred    hadoop             0 2018-10-19 08:35 /user/history
drwxrwxr-t   - hive      hive               0 2018-10-19 08:36 /user/hive
drwxrwxr-x   - hue       hue                0 2018-10-19 08:36 /user/hue
drwxrwxr-x   - oozie     oozie              0 2018-10-19 08:36 /user/oozie
drwxr-xr-x   - raffles   raffles            0 2018-10-19 08:46 /user/raffles
```


### API Call
```
[root@node02 ~]# curl -u admin:admin -X GET http://node02.xpandit.com:7180/api/v14/hosts
{
  "items" : [ {
    "hostId" : "480e051c-4e1d-47ee-b47c-f3783aaa0666",
    "ipAddress" : "20.1.0.4",
    "hostname" : "node01.xpandit.com",
    "rackId" : "/default",
    "hostUrl" : "http://node02.xpandit.com:7180/cmf/hostRedirect/480e051c-4e1d-47ee-b47c-f3783aaa0666",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16810840064
  }, {
    "hostId" : "fe761044-e868-488d-8137-f74a4d9192ce",
    "ipAddress" : "20.1.0.5",
    "hostname" : "node02.xpandit.com",
    "rackId" : "/default",
    "hostUrl" : "http://node02.xpandit.com:7180/cmf/hostRedirect/fe761044-e868-488d-8137-f74a4d9192ce",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16810840064
  }, {
    "hostId" : "500543df-4ca9-4c86-85bd-34642219ad0e",
    "ipAddress" : "20.1.0.6",
    "hostname" : "node03.xpandit.com",
    "rackId" : "/default",
    "hostUrl" : "http://node02.xpandit.com:7180/cmf/hostRedirect/500543df-4ca9-4c86-85bd-34642219ad0e",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16810840064
  }, {
    "hostId" : "36b28e25-9c0e-405e-8019-84ddbabfcf3d",
    "ipAddress" : "20.1.0.7",
    "hostname" : "node04.xpandit.com",
    "rackId" : "/default",
    "hostUrl" : "http://node02.xpandit.com:7180/cmf/hostRedirect/36b28e25-9c0e-405e-8019-84ddbabfcf3d",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16810840064
  }, {
    "hostId" : "a634c5f6-23f8-4c5b-98d0-e2f6b89444f4",
    "ipAddress" : "20.1.0.8",
    "hostname" : "node05.xpandit.com",
    "rackId" : "/default",
    "hostUrl" : "http://node02.xpandit.com:7180/cmf/hostRedirect/a634c5f6-23f8-4c5b-98d0-e2f6b89444f4",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16810840064
  } ]
}
```

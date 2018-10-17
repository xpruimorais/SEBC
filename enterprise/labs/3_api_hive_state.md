## Hive Status

### Command
```
[root@node01 ~]$ curl -u xpruimorais:cloudera -X GET 'http://rdsmsebc01.eastus.cloudapp.azure.com:7180/api/v12/clusters/xpruimorais/services/hive/'
```

### Output
```
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://node01.xpandit.com:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://node01.xpandit.com:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "GOOD_HEALTH"
}
```


## Hive Stop

### Command
```
[root@node01 ~]$ curl -u xpruimorais:cloudera -X POST 'http://rdsmsebc01.eastus.cloudapp.azure.com:7180/api/v12/clusters/xpruimorais/services/hive/commands/stop'
```


### Output
```
{
  "id" : 706,
  "name" : "Stop",
  "startTime" : "2018-10-17T08:54:33.708Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```


## Hive Start

### Command
```
[root@node01 ~]$ curl -u xpruimorais:cloudera -X POST 'http://rdsmsebc01.eastus.cloudapp.azure.com:7180/api/v12/clusters/xpruimorais/services/hive/commands/start'
```


### Output
```
{
  "id" : 710,
  "name" : "Start",
  "startTime" : "2018-10-17T08:56:15.415Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

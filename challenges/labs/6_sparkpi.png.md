```
[raffles@node02 ~]$ spark2-submit --class org.apache.spark.examples.SparkPi --master yarn --deploy-mode cluster /opt/cloudera/parcels/SPARK2/lib/spark2/examples/jars/spark-examples_2.11-2.3.0.cloudera4.jar                                                              10
18/10/19 09:25:46 INFO client.RMProxy: Connecting to ResourceManager at node02.xpandit.com/20.1.0.5:8032
18/10/19 09:25:47 INFO yarn.Client: Requesting a new application from cluster with 3 NodeManagers
18/10/19 09:25:47 INFO yarn.Client: Verifying our application has not requested more than the maximum memory capability of the cluster (6067 MB per container)
18/10/19 09:25:47 INFO yarn.Client: Will allocate AM container, with 1408 MB memory including 384 MB overhead
18/10/19 09:25:47 INFO yarn.Client: Setting up container launch context for our AM
18/10/19 09:25:47 INFO yarn.Client: Setting up the launch environment for our AM container
18/10/19 09:25:47 INFO yarn.Client: Preparing resources for our AM container
18/10/19 09:25:47 INFO yarn.Client: Uploading resource file:/opt/cloudera/parcels/SPARK2/lib/spark2/examples/jars/spark-examples_2.11-2.3.0.cloudera4.jar -> hdfs://node01.xpandit.com:8020/user/raffles/.spar                                                             kStaging/application_1539941025111_0001/spark-examples_2.11-2.3.0.cloudera4.jar
18/10/19 09:25:47 INFO yarn.Client: Uploading resource file:/tmp/spark-28957d20-b16a-45a9-a5ff-8252f48e2eaf/__spark_conf__7477690282594571818.zip -> hdfs://node01.xpandit.com:8020/user/raffles/.sparkStaging                                                             /application_1539941025111_0001/__spark_conf__.zip
18/10/19 09:25:48 INFO spark.SecurityManager: Changing view acls to: raffles
18/10/19 09:25:48 INFO spark.SecurityManager: Changing modify acls to: raffles
18/10/19 09:25:48 INFO spark.SecurityManager: Changing view acls groups to:
18/10/19 09:25:48 INFO spark.SecurityManager: Changing modify acls groups to:
18/10/19 09:25:48 INFO spark.SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users  with view permissions: Set(raffles); groups with view permissions: Set(); users  with modify                                                              permissions: Set(raffles); groups with modify permissions: Set()
18/10/19 09:25:48 INFO security.HadoopFSDelegationTokenProvider: getting token for: DFS[DFSClient[clientName=DFSClient_NONMAPREDUCE_-1187836115_1, ugi=raffles@XPRUIMORAIS.SG (auth:KERBEROS)]]
18/10/19 09:25:48 INFO hdfs.DFSClient: Created token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@XPRUIMORAIS.SG, renewer=yarn, realUser=, issueDate=1539941148192, maxDate=1540545948192, sequenceNumber=                                                             3, masterKeyId=2 on 20.1.0.4:8020
18/10/19 09:25:48 INFO security.HadoopFSDelegationTokenProvider: getting token for: DFS[DFSClient[clientName=DFSClient_NONMAPREDUCE_-1187836115_1, ugi=raffles@XPRUIMORAIS.SG (auth:KERBEROS)]]
18/10/19 09:25:48 INFO hive.metastore: Trying to connect to metastore with URI thrift://node01.xpandit.com:9083
18/10/19 09:25:49 INFO hive.metastore: Opened a connection to metastore, current connections: 1
18/10/19 09:25:49 INFO hive.metastore: Connected to metastore.
18/10/19 09:25:49 INFO hive.metastore: Closed a connection to metastore, current connections: 0
18/10/19 09:25:50 INFO yarn.Client: Submitting application application_1539941025111_0001 to ResourceManager
18/10/19 09:25:51 INFO impl.YarnClientImpl: Submitted application application_1539941025111_0001
18/10/19 09:25:52 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:25:52 INFO yarn.Client:
         client token: N/A
         diagnostics: N/A
         ApplicationMaster host: N/A
         ApplicationMaster RPC port: -1
         queue: root.users.raffles
         start time: 1539941150642
         final status: UNDEFINED
         tracking URL: http://node02.xpandit.com:8088/proxy/application_1539941025111_0001/
         user: raffles
18/10/19 09:25:53 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:25:54 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:25:55 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:25:56 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:25:57 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:25:58 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:25:59 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:26:00 INFO yarn.Client: Application report for application_1539941025111_0001 (state: ACCEPTED)
18/10/19 09:26:01 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:01 INFO yarn.Client:
         client token: Token { kind: YARN_CLIENT_TOKEN, service:  }
         diagnostics: N/A
         ApplicationMaster host: 20.1.0.7
         ApplicationMaster RPC port: 0
         queue: root.users.raffles
         start time: 1539941150642
         final status: UNDEFINED
         tracking URL: http://node02.xpandit.com:8088/proxy/application_1539941025111_0001/
         user: raffles
18/10/19 09:26:02 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:03 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:04 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:05 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:06 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:07 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:08 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:09 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:10 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:11 INFO yarn.Client: Application report for application_1539941025111_0001 (state: RUNNING)
18/10/19 09:26:12 INFO yarn.Client: Application report for application_1539941025111_0001 (state: FINISHED)
18/10/19 09:26:12 INFO yarn.Client:
         client token: N/A
         diagnostics: N/A
         ApplicationMaster host: 20.1.0.7
         ApplicationMaster RPC port: 0
         queue: root.users.raffles
         start time: 1539941150642
         final status: SUCCEEDED
         tracking URL: http://node02.xpandit.com:8088/proxy/application_1539941025111_0001/
         user: raffles
18/10/19 09:26:12 INFO util.ShutdownHookManager: Shutdown hook called
18/10/19 09:26:12 INFO util.ShutdownHookManager: Deleting directory /tmp/spark-28957d20-b16a-45a9-a5ff-8252f48e2eaf
18/10/19 09:26:12 INFO util.ShutdownHookManager: Deleting directory /tmp/spark-9ce2f04e-9eb4-464f-b9b3-ccf96b04e950
```

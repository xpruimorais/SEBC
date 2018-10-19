```
[fullerton@node02 ~]$ yarn jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 10 10
Number of Maps  = 10
Samples per Map = 10
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
18/10/19 09:08:26 INFO client.RMProxy: Connecting to ResourceManager at node02.xpandit.com/20.1.0.5:8032
18/10/19 09:08:27 INFO hdfs.DFSClient: Created token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@XPRUIMORAIS.SG, renewer=yarn, realUser=, issueDate=1539940107164, maxDate=1540544907164, sequenceNumber=2, masterKeyId=2 on 20.1.0.4:8020
18/10/19 09:08:27 INFO security.TokenCache: Got dt for hdfs://node01.xpandit.com:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 20.1.0.4:8020, Ident: (token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@XPRUIMORAIS.SG, renewer=yarn, realUser=, issueDate=1539940107164, maxDate=1540544907164, sequenceNumber=2, masterKeyId=2)
18/10/19 09:08:27 INFO input.FileInputFormat: Total input paths to process : 10
18/10/19 09:08:28 INFO mapreduce.JobSubmitter: number of splits:10
18/10/19 09:08:28 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539939671671_0002
18/10/19 09:08:28 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 20.1.0.4:8020, Ident: (token for fullerton: HDFS_DELEGATION_TOKEN owner=fullerton@XPRUIMORAIS.SG, renewer=yarn, realUser=, issueDate=1539940107164, maxDate=1540544907164, sequenceNumber=2, masterKeyId=2)
18/10/19 09:08:28 INFO impl.YarnClientImpl: Submitted application application_1539939671671_0002
18/10/19 09:08:28 INFO mapreduce.Job: The url to track the job: http://node02.xpandit.com:8088/proxy/application_1539939671671_0002/
18/10/19 09:08:28 INFO mapreduce.Job: Running job: job_1539939671671_0002
18/10/19 09:08:53 INFO mapreduce.Job: Job job_1539939671671_0002 running in uber mode : false
18/10/19 09:08:53 INFO mapreduce.Job:  map 0% reduce 0%
18/10/19 09:09:01 INFO mapreduce.Job:  map 10% reduce 0%
18/10/19 09:09:05 INFO mapreduce.Job:  map 20% reduce 0%
18/10/19 09:09:06 INFO mapreduce.Job:  map 50% reduce 0%
18/10/19 09:09:07 INFO mapreduce.Job:  map 60% reduce 0%
18/10/19 09:09:13 INFO mapreduce.Job:  map 90% reduce 0%
18/10/19 09:09:14 INFO mapreduce.Job:  map 100% reduce 0%
18/10/19 09:09:24 INFO mapreduce.Job:  map 100% reduce 100%
18/10/19 09:09:25 INFO mapreduce.Job: Job job_1539939671671_0002 completed successfully
18/10/19 09:09:25 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=85
                FILE: Number of bytes written=1658190
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=2780
                HDFS: Number of bytes written=215
                HDFS: Number of read operations=43
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=3
        Job Counters
                Launched map tasks=10
                Launched reduce tasks=1
                Data-local map tasks=10
                Total time spent by all maps in occupied slots (ms)=71198
                Total time spent by all reduces in occupied slots (ms)=7136
                Total time spent by all map tasks (ms)=71198
                Total time spent by all reduce tasks (ms)=7136
                Total vcore-milliseconds taken by all map tasks=71198
                Total vcore-milliseconds taken by all reduce tasks=7136
                Total megabyte-milliseconds taken by all map tasks=72906752
                Total megabyte-milliseconds taken by all reduce tasks=7307264
        Map-Reduce Framework
                Map input records=10
                Map output records=20
                Map output bytes=180
                Map output materialized bytes=339
                Input split bytes=1600
                Combine input records=0
                Combine output records=0
                Reduce input groups=2
                Reduce shuffle bytes=339
                Reduce input records=20
                Reduce output records=0
                Spilled Records=40
                Shuffled Maps =10
                Failed Shuffles=0
                Merged Map outputs=10
                GC time elapsed (ms)=1856
                CPU time spent (ms)=10370
                Physical memory (bytes) snapshot=4814999552
                Virtual memory (bytes) snapshot=30700933120
                Total committed heap usage (bytes)=5101322240
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=1180
        File Output Format Counters
                Bytes Written=97
Job Finished in 58.609 seconds
Estimated value of Pi is 3.20000000000000000000
```

```
[raffles@node02 ~]$ yarn jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/raffles/tgen512 /user/raffles/tgen512sort
18/10/19 09:06:17 INFO terasort.TeraSort: starting
18/10/19 09:06:18 INFO hdfs.DFSClient: Created token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@XPRUIMORAIS.SG, renewer=yarn, realUser=, issueDate=1539939978678, maxDate=1540544778678, sequenceNumber=1, masterKeyId=2 on 20.1.0.4:8020
18/10/19 09:06:18 INFO security.TokenCache: Got dt for hdfs://node01.xpandit.com:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 20.1.0.4:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@XPRUIMORAIS.SG, renewer=yarn, realUser=, issueDate=1539939978678, maxDate=1540544778678, sequenceNumber=1, masterKeyId=2)
18/10/19 09:06:18 INFO input.FileInputFormat: Total input paths to process : 6
Spent 471ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 477ms
Sampling 10 splits of 198
Making 6 from 100000 sampled records
Computing parititions took 754ms
Spent 1233ms computing partitions.
18/10/19 09:06:19 INFO client.RMProxy: Connecting to ResourceManager at node02.xpandit.com/20.1.0.5:8032
18/10/19 09:06:20 INFO mapreduce.JobSubmitter: number of splits:198
18/10/19 09:06:20 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539939671671_0001
18/10/19 09:06:20 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 20.1.0.4:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@XPRUIMORAIS.SG, renewer=yarn, realUser=, issueDate=1539939978678, maxDate=1540544778678, sequenceNumber=1, masterKeyId=2)
18/10/19 09:06:21 INFO impl.YarnClientImpl: Submitted application application_1539939671671_0001
18/10/19 09:06:21 INFO mapreduce.Job: The url to track the job: http://node02.xpandit.com:8088/proxy/application_1539939671671_0001/
18/10/19 09:06:21 INFO mapreduce.Job: Running job: job_1539939671671_0001
18/10/19 09:06:31 INFO mapreduce.Job: Job job_1539939671671_0001 running in uber mode : false
18/10/19 09:06:31 INFO mapreduce.Job:  map 0% reduce 0%
18/10/19 09:06:41 INFO mapreduce.Job:  map 1% reduce 0%
18/10/19 09:06:42 INFO mapreduce.Job:  map 2% reduce 0%
18/10/19 09:06:51 INFO mapreduce.Job:  map 5% reduce 0%
18/10/19 09:06:52 INFO mapreduce.Job:  map 6% reduce 0%
18/10/19 09:06:53 INFO mapreduce.Job:  map 7% reduce 0%
18/10/19 09:07:02 INFO mapreduce.Job:  map 8% reduce 0%
18/10/19 09:07:03 INFO mapreduce.Job:  map 10% reduce 0%
18/10/19 09:07:04 INFO mapreduce.Job:  map 13% reduce 0%
18/10/19 09:07:12 INFO mapreduce.Job:  map 14% reduce 0%
18/10/19 09:07:13 INFO mapreduce.Job:  map 15% reduce 0%
18/10/19 09:07:14 INFO mapreduce.Job:  map 16% reduce 0%
18/10/19 09:07:16 INFO mapreduce.Job:  map 17% reduce 0%
18/10/19 09:07:17 INFO mapreduce.Job:  map 18% reduce 0%
18/10/19 09:07:20 INFO mapreduce.Job:  map 19% reduce 0%
18/10/19 09:07:22 INFO mapreduce.Job:  map 20% reduce 0%
18/10/19 09:07:24 INFO mapreduce.Job:  map 21% reduce 0%
18/10/19 09:07:27 INFO mapreduce.Job:  map 22% reduce 0%
18/10/19 09:07:28 INFO mapreduce.Job:  map 23% reduce 0%
18/10/19 09:07:31 INFO mapreduce.Job:  map 25% reduce 0%
18/10/19 09:07:36 INFO mapreduce.Job:  map 26% reduce 0%
18/10/19 09:07:37 INFO mapreduce.Job:  map 27% reduce 0%
18/10/19 09:07:40 INFO mapreduce.Job:  map 28% reduce 0%
18/10/19 09:07:41 INFO mapreduce.Job:  map 29% reduce 0%
18/10/19 09:07:42 INFO mapreduce.Job:  map 30% reduce 0%
18/10/19 09:07:44 INFO mapreduce.Job:  map 31% reduce 0%
18/10/19 09:07:48 INFO mapreduce.Job:  map 32% reduce 0%
18/10/19 09:07:50 INFO mapreduce.Job:  map 33% reduce 0%
18/10/19 09:07:51 INFO mapreduce.Job:  map 35% reduce 0%
18/10/19 09:07:54 INFO mapreduce.Job:  map 36% reduce 0%
18/10/19 09:07:58 INFO mapreduce.Job:  map 37% reduce 0%
18/10/19 09:07:59 INFO mapreduce.Job:  map 39% reduce 0%
18/10/19 09:08:03 INFO mapreduce.Job:  map 40% reduce 0%
18/10/19 09:08:04 INFO mapreduce.Job:  map 41% reduce 0%
18/10/19 09:08:07 INFO mapreduce.Job:  map 42% reduce 0%
18/10/19 09:08:09 INFO mapreduce.Job:  map 43% reduce 0%
18/10/19 09:08:10 INFO mapreduce.Job:  map 44% reduce 0%
18/10/19 09:08:11 INFO mapreduce.Job:  map 45% reduce 0%
18/10/19 09:08:14 INFO mapreduce.Job:  map 46% reduce 0%
18/10/19 09:08:16 INFO mapreduce.Job:  map 47% reduce 0%
18/10/19 09:08:18 INFO mapreduce.Job:  map 48% reduce 0%
18/10/19 09:08:19 INFO mapreduce.Job:  map 49% reduce 0%
18/10/19 09:08:22 INFO mapreduce.Job:  map 50% reduce 0%
18/10/19 09:08:23 INFO mapreduce.Job:  map 51% reduce 0%
18/10/19 09:08:26 INFO mapreduce.Job:  map 52% reduce 0%
18/10/19 09:08:28 INFO mapreduce.Job:  map 53% reduce 0%
18/10/19 09:08:29 INFO mapreduce.Job:  map 54% reduce 0%
18/10/19 09:08:32 INFO mapreduce.Job:  map 55% reduce 0%
18/10/19 09:08:34 INFO mapreduce.Job:  map 56% reduce 0%
18/10/19 09:08:36 INFO mapreduce.Job:  map 57% reduce 0%
18/10/19 09:08:37 INFO mapreduce.Job:  map 58% reduce 0%
18/10/19 09:08:39 INFO mapreduce.Job:  map 59% reduce 0%
18/10/19 09:08:42 INFO mapreduce.Job:  map 60% reduce 0%
18/10/19 09:08:43 INFO mapreduce.Job:  map 61% reduce 0%
18/10/19 09:08:46 INFO mapreduce.Job:  map 62% reduce 0%
18/10/19 09:08:48 INFO mapreduce.Job:  map 63% reduce 0%
18/10/19 09:08:50 INFO mapreduce.Job:  map 64% reduce 0%
18/10/19 09:08:51 INFO mapreduce.Job:  map 65% reduce 0%
18/10/19 09:08:54 INFO mapreduce.Job:  map 66% reduce 0%
18/10/19 09:08:57 INFO mapreduce.Job:  map 67% reduce 0%
18/10/19 09:08:59 INFO mapreduce.Job:  map 68% reduce 0%
18/10/19 09:09:00 INFO mapreduce.Job:  map 69% reduce 0%
18/10/19 09:09:02 INFO mapreduce.Job:  map 70% reduce 0%
18/10/19 09:09:11 INFO mapreduce.Job:  map 71% reduce 0%
18/10/19 09:09:14 INFO mapreduce.Job:  map 72% reduce 0%
18/10/19 09:09:15 INFO mapreduce.Job:  map 73% reduce 0%
18/10/19 09:09:20 INFO mapreduce.Job:  map 74% reduce 0%
18/10/19 09:09:23 INFO mapreduce.Job:  map 75% reduce 0%
18/10/19 09:09:25 INFO mapreduce.Job:  map 77% reduce 0%
18/10/19 09:09:28 INFO mapreduce.Job:  map 78% reduce 0%
18/10/19 09:09:31 INFO mapreduce.Job:  map 79% reduce 0%
18/10/19 09:09:33 INFO mapreduce.Job:  map 80% reduce 0%
18/10/19 09:09:34 INFO mapreduce.Job:  map 81% reduce 0%
18/10/19 09:09:37 INFO mapreduce.Job:  map 82% reduce 0%
18/10/19 09:09:39 INFO mapreduce.Job:  map 83% reduce 0%
18/10/19 09:09:40 INFO mapreduce.Job:  map 84% reduce 0%
18/10/19 09:09:42 INFO mapreduce.Job:  map 85% reduce 0%
18/10/19 09:09:46 INFO mapreduce.Job:  map 86% reduce 0%
18/10/19 09:09:47 INFO mapreduce.Job:  map 87% reduce 0%
18/10/19 09:09:53 INFO mapreduce.Job:  map 88% reduce 0%
18/10/19 09:09:55 INFO mapreduce.Job:  map 88% reduce 4%
18/10/19 09:09:56 INFO mapreduce.Job:  map 89% reduce 4%
18/10/19 09:09:57 INFO mapreduce.Job:  map 89% reduce 9%
18/10/19 09:09:59 INFO mapreduce.Job:  map 89% reduce 13%
18/10/19 09:10:00 INFO mapreduce.Job:  map 90% reduce 22%
18/10/19 09:10:02 INFO mapreduce.Job:  map 91% reduce 22%
18/10/19 09:10:04 INFO mapreduce.Job:  map 91% reduce 23%
18/10/19 09:10:05 INFO mapreduce.Job:  map 91% reduce 24%
18/10/19 09:10:06 INFO mapreduce.Job:  map 92% reduce 25%
18/10/19 09:10:09 INFO mapreduce.Job:  map 93% reduce 25%
18/10/19 09:10:10 INFO mapreduce.Job:  map 94% reduce 26%
18/10/19 09:10:13 INFO mapreduce.Job:  map 95% reduce 26%
18/10/19 09:10:16 INFO mapreduce.Job:  map 96% reduce 26%
18/10/19 09:10:18 INFO mapreduce.Job:  map 97% reduce 27%
18/10/19 09:10:20 INFO mapreduce.Job:  map 98% reduce 27%
18/10/19 09:10:23 INFO mapreduce.Job:  map 99% reduce 27%
18/10/19 09:10:25 INFO mapreduce.Job:  map 100% reduce 27%
18/10/19 09:10:26 INFO mapreduce.Job:  map 100% reduce 33%
18/10/19 09:10:27 INFO mapreduce.Job:  map 100% reduce 39%
18/10/19 09:10:29 INFO mapreduce.Job:  map 100% reduce 52%
18/10/19 09:10:30 INFO mapreduce.Job:  map 100% reduce 58%
18/10/19 09:10:32 INFO mapreduce.Job:  map 100% reduce 59%
18/10/19 09:10:33 INFO mapreduce.Job:  map 100% reduce 61%
18/10/19 09:10:35 INFO mapreduce.Job:  map 100% reduce 66%
18/10/19 09:10:36 INFO mapreduce.Job:  map 100% reduce 72%
18/10/19 09:10:38 INFO mapreduce.Job:  map 100% reduce 75%
18/10/19 09:10:39 INFO mapreduce.Job:  map 100% reduce 77%
18/10/19 09:10:40 INFO mapreduce.Job:  map 100% reduce 79%
18/10/19 09:10:41 INFO mapreduce.Job:  map 100% reduce 81%
18/10/19 09:10:44 INFO mapreduce.Job:  map 100% reduce 83%
18/10/19 09:10:45 INFO mapreduce.Job:  map 100% reduce 85%
18/10/19 09:10:46 INFO mapreduce.Job:  map 100% reduce 86%
18/10/19 09:10:47 INFO mapreduce.Job:  map 100% reduce 87%
18/10/19 09:10:48 INFO mapreduce.Job:  map 100% reduce 88%
18/10/19 09:11:00 INFO mapreduce.Job:  map 100% reduce 95%
18/10/19 09:11:06 INFO mapreduce.Job:  map 100% reduce 97%
18/10/19 09:11:11 INFO mapreduce.Job:  map 100% reduce 100%
18/10/19 09:11:12 INFO mapreduce.Job: Job job_1539939671671_0001 completed successfully
18/10/19 09:11:12 INFO mapreduce.Job: Counters: 49
        File System Counters
                FILE: Number of bytes read=2913728112
                FILE: Number of bytes written=5790615750
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=6553625542
                HDFS: Number of bytes written=6553600000
                HDFS: Number of read operations=612
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=12
        Job Counters
                Launched map tasks=198
                Launched reduce tasks=6
                Data-local map tasks=198
                Total time spent by all maps in occupied slots (ms)=1873199
                Total time spent by all reduces in occupied slots (ms)=366169
                Total time spent by all map tasks (ms)=1873199
                Total time spent by all reduce tasks (ms)=366169
                Total vcore-milliseconds taken by all map tasks=1873199
                Total vcore-milliseconds taken by all reduce tasks=366169
                Total megabyte-milliseconds taken by all map tasks=1918155776
                Total megabyte-milliseconds taken by all reduce tasks=374957056
        Map-Reduce Framework
                Map input records=65536000
                Map output records=65536000
                Map output bytes=6684672000
                Map output materialized bytes=2845961060
                Input split bytes=25542
                Combine input records=0
                Combine output records=0
                Reduce input groups=65536000
                Reduce shuffle bytes=2845961060
                Reduce input records=65536000
                Reduce output records=65536000
                Spilled Records=131072000
                Shuffled Maps =1188
                Failed Shuffles=0
                Merged Map outputs=1188
                GC time elapsed (ms)=47525
                CPU time spent (ms)=1109050
                Physical memory (bytes) snapshot=106484559872
                Virtual memory (bytes) snapshot=569402400768
                Total committed heap usage (bytes)=113837604864
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=6553600000
        File Output Format Counters
                Bytes Written=6553600000
18/10/19 09:11:12 INFO terasort.TeraSort: done
```

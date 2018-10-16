# Teragen and Terasort

## Preparation

```
sudo -u hdfs hdfs dfs -mkdir /user/xpruimorais
sudo -u hdfs hdfs dfs -chown xpruimorais:xpruimorais /user/xpruimorais
[root@node01 ~]# su - xpruimorais
```


## Teragen

```
[xpruimorais@node01 ~]$ time yarn jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Dmapreduce.job.maps=4 -Ddfs.blocksize=33554432 100000000  /user/xpruimorais/teragen10gb
18/10/16 10:23:59 INFO Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
18/10/16 10:23:59 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
18/10/16 10:23:59 INFO terasort.TeraGen: Generating 100000000 using 1
18/10/16 10:23:59 INFO mapreduce.JobSubmitter: number of splits:1
18/10/16 10:23:59 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_local331674511_0001
18/10/16 10:24:00 INFO mapreduce.Job: The url to track the job: http://localhost:8080/
18/10/16 10:24:00 INFO mapreduce.Job: Running job: job_local331674511_0001
18/10/16 10:24:00 INFO mapred.LocalJobRunner: OutputCommitter set in config null
18/10/16 10:24:00 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
18/10/16 10:24:00 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
18/10/16 10:24:00 INFO mapred.LocalJobRunner: OutputCommitter is org.apache.hadoop.mapreduce.lib.output.FileOutputCommitter
18/10/16 10:24:00 INFO mapred.LocalJobRunner: Waiting for map tasks
18/10/16 10:24:00 INFO mapred.LocalJobRunner: Starting task: attempt_local331674511_0001_m_000000_0
18/10/16 10:24:00 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
18/10/16 10:24:00 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
18/10/16 10:24:00 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
18/10/16 10:24:00 INFO mapred.MapTask: Processing split: org.apache.hadoop.examples.terasort.TeraGen$RangeInputFormat$RangeInputSplit@413d3851
18/10/16 10:24:01 INFO mapreduce.Job: Job job_local331674511_0001 running in uber mode : false
18/10/16 10:24:01 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 10:24:12 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:13 INFO mapreduce.Job:  map 9% reduce 0%
18/10/16 10:24:18 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:19 INFO mapreduce.Job:  map 14% reduce 0%
18/10/16 10:24:24 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:25 INFO mapreduce.Job:  map 20% reduce 0%
18/10/16 10:24:30 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:31 INFO mapreduce.Job:  map 25% reduce 0%
18/10/16 10:24:36 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:37 INFO mapreduce.Job:  map 31% reduce 0%
18/10/16 10:24:42 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:43 INFO mapreduce.Job:  map 36% reduce 0%
18/10/16 10:24:48 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:49 INFO mapreduce.Job:  map 41% reduce 0%
18/10/16 10:24:54 INFO mapred.LocalJobRunner: map > map
18/10/16 10:24:55 INFO mapreduce.Job:  map 46% reduce 0%
18/10/16 10:25:00 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:01 INFO mapreduce.Job:  map 52% reduce 0%
18/10/16 10:25:06 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:07 INFO mapreduce.Job:  map 57% reduce 0%
18/10/16 10:25:12 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:13 INFO mapreduce.Job:  map 62% reduce 0%
18/10/16 10:25:18 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:19 INFO mapreduce.Job:  map 67% reduce 0%
18/10/16 10:25:24 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:25 INFO mapreduce.Job:  map 73% reduce 0%
18/10/16 10:25:30 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:31 INFO mapreduce.Job:  map 78% reduce 0%
18/10/16 10:25:36 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:37 INFO mapreduce.Job:  map 83% reduce 0%
18/10/16 10:25:42 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:43 INFO mapreduce.Job:  map 89% reduce 0%
18/10/16 10:25:48 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:49 INFO mapreduce.Job:  map 94% reduce 0%
18/10/16 10:25:54 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:55 INFO mapreduce.Job:  map 99% reduce 0%
18/10/16 10:25:55 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:55 INFO mapred.Task: Task:attempt_local331674511_0001_m_000000_0 is done. And is in the process of committing
18/10/16 10:25:55 INFO mapred.LocalJobRunner: map > map
18/10/16 10:25:55 INFO mapred.Task: Task attempt_local331674511_0001_m_000000_0 is allowed to commit now
18/10/16 10:25:55 INFO output.FileOutputCommitter: Saved output of task 'attempt_local331674511_0001_m_000000_0' to hdfs://node01.xpandit.com:8020/user/xpruimorais/teragen10gb/_temporary/0/task_local331674511_0001_m_000000
18/10/16 10:25:55 INFO mapred.LocalJobRunner: map
18/10/16 10:25:55 INFO mapred.Task: Task 'attempt_local331674511_0001_m_000000_0' done.
18/10/16 10:25:55 INFO mapred.LocalJobRunner: Finishing task: attempt_local331674511_0001_m_000000_0
18/10/16 10:25:55 INFO mapred.LocalJobRunner: map task executor complete.
18/10/16 10:25:56 INFO mapreduce.Job:  map 100% reduce 0%
18/10/16 10:25:56 INFO mapreduce.Job: Job job_local331674511_0001 completed successfully
18/10/16 10:25:56 INFO mapreduce.Job: Counters: 21
        File System Counters
                FILE: Number of bytes read=276519
                FILE: Number of bytes written=626301
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=0
                HDFS: Number of bytes written=10000000000
                HDFS: Number of read operations=4
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=3
        Map-Reduce Framework
                Map input records=100000000
                Map output records=100000000
                Input split bytes=83
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=447
                Total committed heap usage (bytes)=176685056
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=214760662691937609
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=10000000000

real    1m59.506s
user    2m12.098s
sys     0m12.486s
```


## Terasort

```
[xpruimorais@node01 ~]$ time yarn jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/xpruimorais/teragen10gb /user/xpruimorais/terasort10gb_sorted
18/10/16 10:27:59 INFO terasort.TeraSort: starting
18/10/16 10:28:00 INFO input.FileInputFormat: Total input paths to process : 1
Spent 235ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 241ms
Sampling 10 splits of 298
Making 1 from 100000 sampled records
Computing parititions took 692ms
Spent 935ms computing partitions.
18/10/16 10:28:01 INFO Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
18/10/16 10:28:01 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
18/10/16 10:28:02 INFO mapreduce.JobSubmitter: number of splits:298
18/10/16 10:28:02 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_local683935964_0001
18/10/16 10:28:02 INFO mapred.LocalDistributedCacheManager: Creating symlink: /tmp/hadoop-xpruimorais/mapred/local/1539685682329/_partition.lst <- /home/xpruimorais/_partition.lst
18/10/16 10:28:02 INFO mapred.LocalDistributedCacheManager: Localized hdfs://node01.xpandit.com:8020/user/xpruimorais/terasort10gb_sorted/_partition.lst as file:/tmp/hadoop-xpruimorais/mapred/local/153968569/_partition.lst
18/10/16 10:28:02 INFO mapreduce.Job: The url to track the job: http://localhost:8080/
18/10/16 10:28:02 INFO mapreduce.Job: Running job: job_local683935964_0001
18/10/16 10:28:02 INFO mapred.LocalJobRunner: OutputCommitter set in config null
18/10/16 10:28:02 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
18/10/16 10:28:02 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
18/10/16 10:28:02 INFO mapred.LocalJobRunner: OutputCommitter is org.apache.hadoop.mapreduce.lib.output.FileOutputCommitter
18/10/16 10:28:02 INFO mapred.LocalJobRunner: Starting task: attempt_local683935964_0001_m_000000_0
18/10/16 10:28:02 INFO mapred.LocalJobRunner: Waiting for map tasks
18/10/16 10:28:02 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
18/10/16 10:28:02 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
18/10/16 10:28:02 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
18/10/16 10:28:02 INFO mapred.MapTask: Processing split: hdfs://node01.xpandit.com:8020/user/xpruimorais/teragen10gb/part-m-00000:9965666304+34333696
18/10/16 10:28:02 INFO mapred.MapTask: (EQUATOR) 0 kvi 26214396(104857584)
18/10/16 10:28:02 INFO mapred.MapTask: mapreduce.task.io.sort.mb: 100
18/10/16 10:28:02 INFO mapred.MapTask: soft limit at 83886080
18/10/16 10:28:02 INFO mapred.MapTask: bufstart = 0; bufvoid = 104857600
18/10/16 10:28:02 INFO mapred.MapTask: kvstart = 26214396; length = 6553600
18/10/16 10:28:02 INFO mapred.MapTask: Map output collector class = org.apache.hadoop.mapred.MapTask$MapOutputBuffer
18/10/16 10:28:03 INFO mapred.LocalJobRunner:
18/10/16 10:28:03 INFO mapred.MapTask: Starting flush of map output
18/10/16 10:28:03 INFO mapred.MapTask: Spilling map output
18/10/16 10:28:03 INFO mapred.MapTask: bufstart = 0; bufend = 35020272; bufvoid = 104857600
18/10/16 10:28:03 INFO mapred.MapTask: kvstart = 26214396(104857584); kvend = 24841056(99364224); length = 1373341/6553600
18/10/16 10:28:03 INFO mapreduce.Job: Job job_local683935964_0001 running in uber mode : false
18/10/16 10:28:03 INFO mapreduce.Job:  map 0% reduce 0%
...
...
18/10/16 10:46:15 INFO mapreduce.Job:  map 100% reduce 99%
18/10/16 10:46:18 INFO mapred.Task: Task:attempt_local683935964_0001_r_000000_0 is done. And is in the process of committing
18/10/16 10:46:18 INFO mapred.LocalJobRunner: reduce > reduce
18/10/16 10:46:18 INFO mapred.Task: Task attempt_local683935964_0001_r_000000_0 is allowed to commit now
18/10/16 10:46:18 INFO output.FileOutputCommitter: Saved output of task 'attempt_local683935964_0001_r_000000_0' to hdfs://node01.xpandit.com:8020/user/xpruimorais/terasort10gb_sorted/_temporary/0/task_local683935964_0001_r_000000
18/10/16 10:46:18 INFO mapred.LocalJobRunner: reduce > reduce
18/10/16 10:46:18 INFO mapred.Task: Task 'attempt_local683935964_0001_r_000000_0' done.
18/10/16 10:46:18 INFO mapred.LocalJobRunner: Finishing task: attempt_local683935964_0001_r_000000_0
18/10/16 10:46:18 INFO mapred.LocalJobRunner: reduce task executor complete.
18/10/16 10:46:18 INFO mapreduce.Job:  map 100% reduce 100%
18/10/16 10:46:19 INFO mapreduce.Job: Job job_local683935964_0001 completed successfully
18/10/16 10:46:19 INFO mapreduce.Job: Counters: 35
        File System Counters
                FILE: Number of bytes read=27437548827
                FILE: Number of bytes written=1582279781247
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=1508105708600
                HDFS: Number of bytes written=10000000000
                HDFS: Number of read operations=97176
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=600
        Map-Reduce Framework
                Map input records=100000000
                Map output records=100000000
                Map output bytes=10200000000
                Map output materialized bytes=10400001788
                Input split bytes=40826
                Combine input records=0
                Combine output records=0
                Reduce input groups=100000000
                Reduce shuffle bytes=10400001788
                Reduce input records=100000000
                Reduce output records=100000000
                Spilled Records=261069058
                Shuffled Maps =298
                Failed Shuffles=0
                Merged Map outputs=298
                GC time elapsed (ms)=19735
                Total committed heap usage (bytes)=309658124288
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=10000000000
        File Output Format Counters
                Bytes Written=10000000000
18/10/16 10:46:19 INFO terasort.TeraSort: done

real    18m21.634s
user    10m2.503s
sys     1m8.924s
```

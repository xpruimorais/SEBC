# Replication

Added user `xpruimorais` in all nodes:

```
ansible -a "useradd -u 1050 xpruimorais" all
```

Created HDFS directories:
```
sudo -u hdfs hdfs dfs -mkdir /tmp/xpruimorais
sudo -u hdfs hdfs dfs -mkdir /tmp/gmspinheiro
sudo -u hdfs hdfs dfs -chown xpruimorais:xpruimorais /tmp/xpruimorais
sudo -u hdfs hdfs dfs -chown xpruimorais:xpruimorais /tmp/gmspinheiro
```

Generated 500MB file using `teragen`:
```
sudo -u xpruimorais hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen 5000000 /tmp/xpruimorais/teragen500mb
```

Ran `distcp` to copy generated file to `/tmp/gmspinheiro/` in the same cluster:
```
[root@node01 ~]# sudo -u xpruimorais hadoop distcp hdfs://node01.xpandit.com:8020/tmp/xpruimorais/teragen500mb hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb
18/10/16 10:13:07 INFO tools.OptionsParser: parseChunkSize: blocksperchunk false
18/10/16 10:13:08 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://node01.xpandit.com:8020/tmp/xpruimorais/teragen500mb], targetPath=hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb, targetPathExists=false, filtersFile='null', blocksPerChunk=0, copyBufferSize=8192}
18/10/16 10:13:08 INFO Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
18/10/16 10:13:08 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
18/10/16 10:13:08 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 3; dirCnt = 1
18/10/16 10:13:08 INFO tools.SimpleCopyListing: Build file listing completed.
18/10/16 10:13:08 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
18/10/16 10:13:08 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
18/10/16 10:13:08 INFO tools.DistCp: Number of paths in the copy list: 3
18/10/16 10:13:08 INFO tools.DistCp: Number of paths in the copy list: 3
18/10/16 10:13:08 INFO jvm.JvmMetrics: Cannot initialize JVM Metrics with processName=JobTracker, sessionId= - already initialized
18/10/16 10:13:09 INFO mapreduce.JobSubmitter: number of splits:1
18/10/16 10:13:09 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_local302815391_0001
18/10/16 10:13:09 INFO mapreduce.Job: The url to track the job: http://localhost:8080/
18/10/16 10:13:09 INFO tools.DistCp: DistCp job-id: job_local302815391_0001
18/10/16 10:13:09 INFO mapreduce.Job: Running job: job_local302815391_0001
18/10/16 10:13:09 INFO mapred.LocalJobRunner: OutputCommitter set in config null
18/10/16 10:13:09 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
18/10/16 10:13:09 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
18/10/16 10:13:09 INFO mapred.LocalJobRunner: OutputCommitter is org.apache.hadoop.tools.mapred.CopyCommitter
18/10/16 10:13:09 INFO mapred.LocalJobRunner: Waiting for map tasks
18/10/16 10:13:09 INFO mapred.LocalJobRunner: Starting task: attempt_local302815391_0001_m_000000_0
18/10/16 10:13:09 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
18/10/16 10:13:09 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
18/10/16 10:13:09 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
18/10/16 10:13:09 INFO mapred.MapTask: Processing split: file:/tmp/hadoop-xpruimorais/mapred/staging/xpruimorais322671176/.staging/_distcp-1601955911/fileList.seq:0+635
18/10/16 10:13:09 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
18/10/16 10:13:09 INFO output.FileOutputCommitter: FileOutputCommitter skip cleanup _temporary folders under output directory:false, ignore cleanup failures: false
18/10/16 10:13:09 INFO mapred.CopyMapper: Copying hdfs://node01.xpandit.com:8020/tmp/xpruimorais/teragen500mb to hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb
18/10/16 10:13:09 INFO mapred.CopyMapper: Copying hdfs://node01.xpandit.com:8020/tmp/xpruimorais/teragen500mb/_SUCCESS to hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb/_SUCCESS
18/10/16 10:13:09 INFO mapred.RetriableFileCopyCommand: Creating temp file: hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb/.distcp.tmp.attempt_local302815391_0001_m_000000_0
18/10/16 10:13:09 INFO mapred.CopyMapper: Copying hdfs://node01.xpandit.com:8020/tmp/xpruimorais/teragen500mb/part-m-00000 to hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb/part-m-00000
18/10/16 10:13:09 INFO mapred.RetriableFileCopyCommand: Creating temp file: hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb/.distcp.tmp.attempt_local302815391_0001_m_000000_0
18/10/16 10:13:10 INFO mapreduce.Job: Job job_local302815391_0001 running in uber mode : false
18/10/16 10:13:10 INFO mapreduce.Job:  map 0% reduce 0%
18/10/16 10:13:15 INFO mapred.LocalJobRunner:
18/10/16 10:13:15 INFO mapred.Task: Task:attempt_local302815391_0001_m_000000_0 is done. And is in the process of committing
18/10/16 10:13:15 INFO mapred.LocalJobRunner:
18/10/16 10:13:15 INFO mapred.Task: Task attempt_local302815391_0001_m_000000_0 is allowed to commit now
18/10/16 10:13:15 INFO output.FileOutputCommitter: Saved output of task 'attempt_local302815391_0001_m_000000_0' to file:/tmp/hadoop-xpruimorais/mapred/staging/xpruimorais322671176/.staging/_distcp-1601955911/_logs/_temporary/0/task_local302815391_0001_m_000000
18/10/16 10:13:15 INFO mapred.LocalJobRunner: 100.0% Copying hdfs://node01.xpandit.com:8020/tmp/xpruimorais/teragen500mb/part-m-00000 to hdfs://node01.xpandit.com:8020/tmp/gmspinheiro/teragen500mb/part-m-00000 [476.8M/476.8M]
18/10/16 10:13:15 INFO mapred.Task: Task 'attempt_local302815391_0001_m_000000_0' done.
18/10/16 10:13:15 INFO mapred.LocalJobRunner: Finishing task: attempt_local302815391_0001_m_000000_0
18/10/16 10:13:15 INFO mapred.LocalJobRunner: map task executor complete.
18/10/16 10:13:15 INFO mapred.CopyCommitter: concat file chunks ...
18/10/16 10:13:15 INFO mapreduce.Job:  map 100% reduce 0%
18/10/16 10:13:15 INFO mapred.CopyCommitter: Cleaning up temporary work folder: file:/tmp/hadoop-xpruimorais/mapred/staging/xpruimorais322671176/.staging/_distcp-1601955911
18/10/16 10:13:16 INFO mapreduce.Job: Job job_local302815391_0001 completed successfully
18/10/16 10:13:16 INFO mapreduce.Job: Counters: 23
        File System Counters
                FILE: Number of bytes read=1970658
                FILE: Number of bytes written=2341213
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=500000000
                HDFS: Number of bytes written=500000000
                HDFS: Number of read operations=25
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=5
        Map-Reduce Framework
                Map input records=3
                Map output records=0
                Input split bytes=170
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=65
                Total committed heap usage (bytes)=182976512
        File Input Format Counters
                Bytes Read=671
        File Output Format Counters
                Bytes Written=8
        DistCp Counters
                Bytes Copied=500000000
                Bytes Expected=500000000
                Files Copied=3
```


Performed `hdfs fsck` in both source and destination:
```
[root@node01 ~]# sudo -u hdfs hdfs fsck /tmp/xpruimorais/teragen500mb -files -blocks
Connecting to namenode via http://node01.xpandit.com:50070/fsck?ugi=hdfs&files=1&blocks=1&path=%2Ftmp%2Fxpruimorais%2Fteragen500mb
FSCK started by hdfs (auth:SIMPLE) from /10.1.0.4 for path /tmp/xpruimorais/teragen500mb at Tue Oct 16 10:16:27 UTC 2018
/tmp/xpruimorais/teragen500mb <dir>
/tmp/xpruimorais/teragen500mb/_SUCCESS 0 bytes, 0 block(s):  OK

/tmp/xpruimorais/teragen500mb/part-m-00000 500000000 bytes, 4 block(s):  OK
0. BP-1166775133-10.1.0.4-1539682262001:blk_1073742562_1738 len=134217728 Live_repl=3
1. BP-1166775133-10.1.0.4-1539682262001:blk_1073742563_1739 len=134217728 Live_repl=3
2. BP-1166775133-10.1.0.4-1539682262001:blk_1073742564_1740 len=134217728 Live_repl=3
3. BP-1166775133-10.1.0.4-1539682262001:blk_1073742565_1741 len=97346816 Live_repl=3

Status: HEALTHY
 Total size:    500000000 B
 Total dirs:    1
 Total files:   2
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 125000000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Oct 16 10:16:27 UTC 2018 in 1 milliseconds


The filesystem under path '/tmp/xpruimorais/teragen500mb' is HEALTHY
[root@node01 ~]# sudo -u hdfs hdfs fsck /tmp/gmspinheiro/teragen500mb -files -blocks
Connecting to namenode via http://node01.xpandit.com:50070/fsck?ugi=hdfs&files=1&blocks=1&path=%2Ftmp%2Fgmspinheiro%2Fteragen500mb
FSCK started by hdfs (auth:SIMPLE) from /10.1.0.4 for path /tmp/gmspinheiro/teragen500mb at Tue Oct 16 10:16:46 UTC 2018
/tmp/gmspinheiro/teragen500mb <dir>
/tmp/gmspinheiro/teragen500mb/_SUCCESS 0 bytes, 0 block(s):  OK

/tmp/gmspinheiro/teragen500mb/part-m-00000 500000000 bytes, 4 block(s):  OK
0. BP-1166775133-10.1.0.4-1539682262001:blk_1073742579_1755 len=134217728 Live_repl=3
1. BP-1166775133-10.1.0.4-1539682262001:blk_1073742580_1756 len=134217728 Live_repl=3
2. BP-1166775133-10.1.0.4-1539682262001:blk_1073742581_1757 len=134217728 Live_repl=3
3. BP-1166775133-10.1.0.4-1539682262001:blk_1073742582_1758 len=97346816 Live_repl=3

Status: HEALTHY
 Total size:    500000000 B
 Total dirs:    1
 Total files:   2
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 125000000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          3
 Number of racks:               1
FSCK ended at Tue Oct 16 10:16:46 UTC 2018 in 1 milliseconds


The filesystem under path '/tmp/gmspinheiro/teragen500mb' is HEALTHY
```

# Snapshots

```
[root@node01 ~]# sudo -u hdfs hdfs dfs -mkdir /tmp/precious
[root@node01 ~]# sudo -u hdfs hdfs dfs -put /tmp/SEBC.zip /tmp/precious/
[root@node01 ~]# sudo -u hdfs hdfs dfsadmin -allowSnapshot /tmp/precious
[root@node01 ~]# sudo -u hdfs hdfs dfsadmin -allowSnapshot /tmp/precious/
Allowing snaphot on /tmp/precious/ succeeded
[root@node01 ~]# sudo -u hdfs hdfs dfs -createSnapshot /tmp/precious/ sebc-hdfs-test
Created snapshot /tmp/precious/.snapshot/sebc-hdfs-test
[root@node01 ~]# sudo -u hdfs hdfs dfs -rm -r /tmp/precious/
rm: Failed to move to trash: hdfs://node01.xpandit.com:8020/tmp/precious: The directory /tmp/precious cannot be deleted since /tmp/precious is snapshottable and already has snapshots
[root@node01 ~]# sudo -u hdfs hdfs dfs -rm -r /tmp/precious/SEBC.zip
18/10/16 11:25:12 INFO fs.TrashPolicyDefault: Moved: 'hdfs://node01.xpandit.com:8020/tmp/precious/SEBC.zip' to trash at: hdfs://node01.xpandit.com:8020/user/hdfs/.Trash/Current/tmp/precious/SEBC.zip
[root@node01 ~]# sudo -u hdfs hdfs dfs -ls /tmp/precious/.snapshot/sebc-hdfs-test
Found 1 items
-rw-r--r--   3 hdfs supergroup    1720611 2018-10-16 11:11 /tmp/precious/.snapshot/sebc-hdfs-test/SEBC.zip
[root@node01 ~]# sudo -u hdfs hdfs dfs -cp /tmp/precious/.snapshot/sebc-hdfs-test/SEBC.zip /tmp/precious/
```

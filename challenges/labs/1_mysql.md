### MariaDB Hostname
```
[root@node01 ~]# hostname
node01.xpandit.com
```

### DB Version
```
[root@node01 ~]# mysql --version
mysql  Ver 15.1 Distrib 5.5.60-MariaDB, for Linux (x86_64) using readline 5.1
```


### List Databases
```
[root@node01 ~]# mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 10
Server version: 5.5.60-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)
```

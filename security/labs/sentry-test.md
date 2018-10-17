
### Step 1
```
[root@node01 ~]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
scan complete in 2ms
Connecting to jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://node02.xpandit.com:10000/defa> show tables;
INFO  : Compiling command(queryId=hive_20181017151616_63e82dc9-7da6-4fc1-9f71-288acb376f9f): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017151616_63e82dc9-7da6-4fc1-9f71-288acb376f9f); Time taken: 0.072 seconds
INFO  : Executing command(queryId=hive_20181017151616_63e82dc9-7da6-4fc1-9f71-288acb376f9f): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017151616_63e82dc9-7da6-4fc1-9f71-288acb376f9f); Time taken: 0.185 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (0.381 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa>
```

### Step 2

```
0: jdbc:hive2://node02.xpandit.com:10000/defa> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181017151919_910fddee-9ffc-43ff-ab5c-5e808ac15a17): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017151919_910fddee-9ffc-43ff-ab5c-5e808ac15a17); Time taken: 0.083 seconds
INFO  : Executing command(queryId=hive_20181017151919_910fddee-9ffc-43ff-ab5c-5e808ac15a17): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017151919_910fddee-9ffc-43ff-ab5c-5e808ac15a17); Time taken: 0.204 seconds
INFO  : OK
No rows affected (0.306 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181017151919_8b827b33-744c-4b62-88dc-59d7ef7e543b): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017151919_8b827b33-744c-4b62-88dc-59d7ef7e543b); Time taken: 0.097 seconds
INFO  : Executing command(queryId=hive_20181017151919_8b827b33-744c-4b62-88dc-59d7ef7e543b): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017151919_8b827b33-744c-4b62-88dc-59d7ef7e543b); Time taken: 0.125 seconds
INFO  : OK
No rows affected (0.237 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa> GRANT ROLE sentry_admin TO GROUP xpruimorais;
INFO  : Compiling command(queryId=hive_20181017151919_12b350f5-4b7d-4c4c-a16b-6ffab03275c2): GRANT ROLE sentry_admin TO GROUP xpruimorais
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017151919_12b350f5-4b7d-4c4c-a16b-6ffab03275c2); Time taken: 0.079 seconds
INFO  : Executing command(queryId=hive_20181017151919_12b350f5-4b7d-4c4c-a16b-6ffab03275c2): GRANT ROLE sentry_admin TO GROUP xpruimorais
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017151919_12b350f5-4b7d-4c4c-a16b-6ffab03275c2); Time taken: 0.07 seconds
INFO  : OK
No rows affected (0.161 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181017152020_e0bd31f9-46ee-475b-97c2-36c04053ffb0): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152020_e0bd31f9-46ee-475b-97c2-36c04053ffb0); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20181017152020_e0bd31f9-46ee-475b-97c2-36c04053ffb0): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152020_e0bd31f9-46ee-475b-97c2-36c04053ffb0); Time taken: 0.125 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.211 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa>
```


### Step 3

```
[root@node01 ~]# ansible -a "groupadd selector" all
[root@node01 ~]# ansible -a "groupadd inserters" all
[root@node01 ~]# ansible -a "useradd -u 1100 -g selector george" all
[root@node01 ~]# ansible -a "useradd -u 1200 -g inserters ferdinand" all
[root@node01 ~]# kadmin.local
Authenticating as principal xpruimorais/admin@XPRUIMORAIS.SEBC.ES with password.
kadmin.local:  add_principal george
WARNING: no policy specified for george@XPRUIMORAIS.SEBC.ES; defaulting to no policy
Enter password for principal "george@XPRUIMORAIS.SEBC.ES":
Re-enter password for principal "george@XPRUIMORAIS.SEBC.ES":
Principal "george@XPRUIMORAIS.SEBC.ES" created.
kadmin.local:  add_principal ferdinand
WARNING: no policy specified for ferdinand@XPRUIMORAIS.SEBC.ES; defaulting to no policy
Enter password for principal "ferdinand@XPRUIMORAIS.SEBC.ES":
Re-enter password for principal "ferdinand@XPRUIMORAIS.SEBC.ES":
Principal "ferdinand@XPRUIMORAIS.SEBC.ES" created.
```

### Step 4

```
[root@node01 ~]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
scan complete in 3ms
Connecting to jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://node02.xpandit.com:10000/defa> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20181017152424_88b4b57b-5c1f-43c2-8120-3a2dfa9a4b20): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152424_88b4b57b-5c1f-43c2-8120-3a2dfa9a4b20); Time taken: 0.084 seconds
INFO  : Executing command(queryId=hive_20181017152424_88b4b57b-5c1f-43c2-8120-3a2dfa9a4b20): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152424_88b4b57b-5c1f-43c2-8120-3a2dfa9a4b20); Time taken: 0.039 seconds
INFO  : OK
No rows affected (0.189 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20181017152424_099c7514-d115-4d0d-b348-4052790f74b9): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152424_099c7514-d115-4d0d-b348-4052790f74b9); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20181017152424_099c7514-d115-4d0d-b348-4052790f74b9): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152424_099c7514-d115-4d0d-b348-4052790f74b9); Time taken: 0.018 seconds
INFO  : OK
No rows affected (0.095 seconds)
```


### Step 5
```
[root@node01 ~]# kinit xpruimorais
Password for xpruimorais@XPRUIMORAIS.SEBC.ES:
[root@node01 ~]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
scan complete in 3ms
Connecting to jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://node02.xpandit.com:10000/defa> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20181017152929_ba415de3-c341-40e2-9738-3a10f61fb25b): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152929_ba415de3-c341-40e2-9738-3a10f61fb25b); Time taken: 0.073 seconds
INFO  : Executing command(queryId=hive_20181017152929_ba415de3-c341-40e2-9738-3a10f61fb25b): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152929_ba415de3-c341-40e2-9738-3a10f61fb25b); Time taken: 0.019 seconds
INFO  : OK
No rows affected (0.163 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20181017152929_e9c3ecf5-94f4-413f-a16c-6a9028350d10): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152929_e9c3ecf5-94f4-413f-a16c-6a9028350d10); Time taken: 0.059 seconds
INFO  : Executing command(queryId=hive_20181017152929_e9c3ecf5-94f4-413f-a16c-6a9028350d10): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152929_e9c3ecf5-94f4-413f-a16c-6a9028350d10); Time taken: 0.017 seconds
INFO  : OK
No rows affected (0.088 seconds)
```



### Step 6
```
0: jdbc:hive2://node02.xpandit.com:10000/defa> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20181017152525_d1812a48-cbfd-437d-b87e-0c808291bba8): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152525_d1812a48-cbfd-437d-b87e-0c808291bba8); Time taken: 0.073 seconds
INFO  : Executing command(queryId=hive_20181017152525_d1812a48-cbfd-437d-b87e-0c808291bba8): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152525_d1812a48-cbfd-437d-b87e-0c808291bba8); Time taken: 0.055 seconds
INFO  : OK
No rows affected (0.141 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20181017152626_08af3ada-5a0c-454f-9d52-3281d1fe0357): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152626_08af3ada-5a0c-454f-9d52-3281d1fe0357); Time taken: 0.075 seconds
INFO  : Executing command(queryId=hive_20181017152626_08af3ada-5a0c-454f-9d52-3281d1fe0357): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152626_08af3ada-5a0c-454f-9d52-3281d1fe0357); Time taken: 0.024 seconds
INFO  : OK
No rows affected (0.113 seconds)
0: jdbc:hive2://node02.xpandit.com:10000/defa> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20181017152626_0e3859e0-faa6-4718-b1d7-1bfb2d3ad93e): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017152626_0e3859e0-faa6-4718-b1d7-1bfb2d3ad93e); Time taken: 0.091 seconds
INFO  : Executing command(queryId=hive_20181017152626_0e3859e0-faa6-4718-b1d7-1bfb2d3ad93e): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017152626_0e3859e0-faa6-4718-b1d7-1bfb2d3ad93e); Time taken: 0.02 seconds
INFO  : OK
No rows affected (0.125 seconds)
```


### Step 7
```
[root@node01 ~]# kinit george
Password for george@XPRUIMORAIS.SEBC.ES:
[root@node01 ~]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
scan complete in 2ms
Connecting to jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://node02.xpandit.com:10000/defa> show tables;
INFO  : Compiling command(queryId=hive_20181017153737_d747f1ec-d902-49be-b650-be4228e77e1f): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017153737_d747f1ec-d902-49be-b650-be4228e77e1f); Time taken: 0.079 seconds
INFO  : Executing command(queryId=hive_20181017153737_d747f1ec-d902-49be-b650-be4228e77e1f): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017153737_d747f1ec-d902-49be-b650-be4228e77e1f); Time taken: 0.152 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.335 seconds)
```


```
[root@node01 ~]# kinit ferdinand
Password for ferdinand@XPRUIMORAIS.SEBC.ES:
[root@node01 ~]# beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
scan complete in 3ms
Connecting to jdbc:hive2://node02.xpandit.com:10000/default;principal=hive/node02.xpandit.com@XPRUIMORAIS.SEBC.ES
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://node02.xpandit.com:10000/defa> show tables;
INFO  : Compiling command(queryId=hive_20181017153939_50d0aa1d-16d6-4e30-8581-f583dafdfc40): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017153939_50d0aa1d-16d6-4e30-8581-f583dafdfc40); Time taken: 0.071 seconds
INFO  : Executing command(queryId=hive_20181017153939_50d0aa1d-16d6-4e30-8581-f583dafdfc40): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017153939_50d0aa1d-16d6-4e30-8581-f583dafdfc40); Time taken: 0.134 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.332 seconds)
```

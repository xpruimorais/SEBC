### Repos
```
[root@node02 ~]# ls /etc/yum.repos.d
CentOS-Base.repo  CentOS-CR.repo  CentOS-Debuginfo.repo  CentOS-fasttrack.repo  CentOS-Media.repo  CentOS-Sources.repo  CentOS-Vault.repo  cloudera-manager.repo  OpenLogic.repo
```


### Prepare DB
```
[root@node02 ~]# /usr/share/cmf/schema/scm_prepare_database.sh mysql --host node01.xpandit.com scm scm scm_password
JAVA_HOME=/usr/java/jdk1.8.0_162
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_162/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!
```

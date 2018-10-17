### What is ubertask optimization?
Ubertask optimization is the ability to run "sufficiently small" jobs sequentially within a single JVM. The term "small" is defined by the threshold for number of maps (`mapreduce.job.ubertask.maxmaps`), the threshold for number of reduces (`mapreduce.job.ubertask.maxreduces`) and the threshold for number of input bytes (`mapreduce.job.ubertask.maxbytes `).


### Where in CM is the Kerberos Security Realm value displayed?
`Administration` > `Settings` > `Category: Kerberos` > `Kerberos Security Realm`


### Which CDH service(s) host a property for enabling Kerberos authentication?

All CDH services have Kerberos related properties. In the current cluster we have:
- Zookeeper: "Enable Kerberos Authentication" - `enableSecurity`
- HDFS and YARN: "Enable Kerberos Authentication for HTTP Web-Consoles"
- All services have the "Kerberos Principal" property


### How do you upgrade the CM agents?
CM agents can be upgraded in two ways:
- Using Cloudera Manager upgrade wizard: `Hosts` > `Re-run Upgrade Wizard`.
- Via command line by installing the packages manually.


### Give the tsquery statement used to chart Hue's CPU utilization?

```select cpu_system_rate + cpu_user_rate where category=ROLE and serviceName="hue"```


### Name all the roles that make up the Hive service

- HiveServer2
- Hive Metastore Server
- Gateway
- WebHCat Server


### What steps must be completed before integrating Cloudera Manager with Kerberos?

- Set up a working KDC (either MIT KDC or Active Directory).
- Configure the KDC to have non-zero ticket lifetime and renewal lifetime.
- Install OpenLdap client libraries on the Cloudera Manager Server host if AD is to be used.
- Install Kerberos client libraries in all hosts.
- Create a Kerberos account that has permissions to create other accounts in the KDC.

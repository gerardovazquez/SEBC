# Treasure Hunt

* What is ubertask optimization?

From Cloudera Manager Yrn configuration help
```sh
Whether to enable ubertask optimization, which runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.
```

This setting is usefull when your task will need to deal with small amounts of data, insted of distributing the task all the maps and the reduce (max. 1 in CDH) if any will run in the same JVM

* Where in CM is the Kerberos Security Realm value displayed?

Adminitration > Settings > Kerberos

* Which CDH service(s) host a property for enabling Kerberos authentication?

All service uses kerberos principal for service authentication when kerberos is enabled but Zookeeper has an enable security switch

* How do you upgrade the CM agents?

In Hosts > Re-Run Upgrade Wizard

* Give the tsquery statement used to chart Hue's CPU utilization?

Click on Hue service,  click on CPU usage chart and select "View Entity Chart"
```sh
SELECT cpu_system_rate + cpu_user_rate WHERE entityName = "hue-HUE_SERVER-452eae34bcba1d443ead04e5acf276ef" AND category = ROLE
```

* Name all the roles that make up the Hive service

In the installed cluster
```sh
Gateway
Hive Metastore
HiveServer2
```
could also be present
```sh
WebHCat Server
```

* What steps must be completed before integrating Cloudera Manager with Kerberos?

Check documentation https://www.cloudera.com/documentation/enterprise/5-8-x/topics/cm_sg_intro_kerb.html#xd_583c10bfdbd326ba--6eed2fb8-14349d04bee--76dd

You need:
-- Set up a working KDC. Cloudera Manager supports MIT KDC and Active Directory.
-- The KDC should be configured to have non-zero ticket lifetime and renewal lifetime. CDH will not work properly if tickets are not renewable.
-- OpenLdap client libraries should be installed on the Cloudera Manager Server host if you want to use Active Directory. Also, Kerberos client libraries should be installed on ALL hosts.
-- Cloudera Manager needs an account that has permissions to create other accounts in the KDC.
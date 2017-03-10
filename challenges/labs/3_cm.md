# Install CDH


* The command and output for hdfs dfs -ls /user

```sh
[root@ip-10-0-1-107 ~]# sudo -u neymar hdfs dfs -ls /user
Found 6 items
drwxrwxrwx   - mapred  hadoop           0 2017-03-10 09:48 /user/history
drwxrwxr-t   - hive    hive             0 2017-03-10 09:49 /user/hive
drwxrwxr-x   - hue     hue              0 2017-03-10 09:49 /user/hue
drwxr-x---   - neymar  neymar           0 2017-03-10 09:50 /user/neymar
drwxrwxr-x   - oozie   oozie            0 2017-03-10 09:49 /user/oozie
drwxr-x---   - ronaldo ronaldo          0 2017-03-10 09:51 /user/ronaldo
```


* The output from the CM API call ../api/v14/hosts

```json
{
  "items" : [ {
    "hostId" : "i-020b12dfd3cc9245d",
    "ipAddress" : "10.0.1.107",
    "hostname" : "ip-10-0-1-107.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-1-156.eu-west-1.compute.internal:7180/cmf/hostRedirect/i-020b12dfd3cc9245d",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "i-0790b37fa578057e7",
    "ipAddress" : "10.0.1.156",
    "hostname" : "ip-10-0-1-156.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-1-156.eu-west-1.compute.internal:7180/cmf/hostRedirect/i-0790b37fa578057e7",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "i-0ae669bc158a04f88",
    "ipAddress" : "10.0.1.179",
    "hostname" : "ip-10-0-1-179.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-1-156.eu-west-1.compute.internal:7180/cmf/hostRedirect/i-0ae669bc158a04f88",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "i-09ca3e9c3b86ff63d",
    "ipAddress" : "10.0.1.204",
    "hostname" : "ip-10-0-1-204.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-1-156.eu-west-1.compute.internal:7180/cmf/hostRedirect/i-09ca3e9c3b86ff63d",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  }, {
    "hostId" : "i-0cc9015b2055122bd",
    "ipAddress" : "10.0.1.78",
    "hostname" : "ip-10-0-1-78.eu-west-1.compute.internal",
    "rackId" : "/default",
    "hostUrl" : "http://ip-10-0-1-156.eu-west-1.compute.internal:7180/cmf/hostRedirect/i-0cc9015b2055122bd",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15740305408
  } ]
}
```

* Error Found after deployuing the CDH

Hive Metasore Canary error: Unable to create the test table

Followed this to solve http://community.cloudera.com/t5/Cloudera-Manager-Installation/The-Hive-Metastore-canary-failed-to-create-a-database/m-p/50589
# Sentry Lab

## Pre-requisites

* Create external database [Done in Install Labs]

* Create hdfs principal and secure /user/hive/warehouse

```sh
[root@ip-10-0-1-128 ~]# hdfs dfs -chmod -R 771 /user/hive/warehouse
[root@ip-10-0-1-128 ~]# hdfs dfs -chown -R hive:hive /user/hive/warehouse
```

* Disable impersonation for HiveServer2 in the Cloudera Manager Admin Console

* If you are using YARN, enable the Hive user to submit YARN jobs. 

* Deploy sentry service

* Add personal user to sentry.service.admin.group

* Enabling the Sentry Service for Hive

* Enabling the Sentry Service for Hue

* Add the Hive, Impala and Hue Groups to Sentry's Admin Groups

* Restart services

# Connect to Hive

```sh
beeline> !connect jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM
scan complete in 3ms
Connecting to jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM
Enter username for jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM: gerardovazquez
Enter password for jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.4)
Driver: Hive JDBC (version 1.1.0-cdh5.8.4)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> 
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> show tables;
INFO  : Compiling command(queryId=hive_20170309095959_0be74556-94ae-472b-9ddf-c82f30a13f18): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170309095959_0be74556-94ae-472b-9ddf-c82f30a13f18); Time taken: 0.792 seconds
INFO  : Executing command(queryId=hive_20170309095959_0be74556-94ae-472b-9ddf-c82f30a13f18): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309095959_0be74556-94ae-472b-9ddf-c82f30a13f18); Time taken: 0.309 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (1,497 seconds)

```

* Add permissions

```sh
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20170309100000_3ce1dc0f-3dc6-4f88-b460-614a73bf60d7): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100000_3ce1dc0f-3dc6-4f88-b460-614a73bf60d7); Time taken: 0.081 seconds
INFO  : Executing command(queryId=hive_20170309100000_3ce1dc0f-3dc6-4f88-b460-614a73bf60d7): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100000_3ce1dc0f-3dc6-4f88-b460-614a73bf60d7); Time taken: 0.53 seconds
INFO  : OK
No rows affected (0,62 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20170309100000_14724921-cd1e-4aae-bb6c-f976ee2e4c26): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100000_14724921-cd1e-4aae-bb6c-f976ee2e4c26); Time taken: 0.092 seconds
INFO  : Executing command(queryId=hive_20170309100000_14724921-cd1e-4aae-bb6c-f976ee2e4c26): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100000_14724921-cd1e-4aae-bb6c-f976ee2e4c26); Time taken: 0.117 seconds
INFO  : OK
No rows affected (0,22 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> GRANT ROLE sentry_admin TO GROUP gerardovazquez
. . . . . . . . . . . . . . . . . . . . . . .> ;
INFO  : Compiling command(queryId=hive_20170309100000_2ae61055-08bc-4dae-9642-2fa90492e264): GRANT ROLE sentry_admin TO GROUP gerardovazquez
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100000_2ae61055-08bc-4dae-9642-2fa90492e264); Time taken: 0.078 seconds
INFO  : Executing command(queryId=hive_20170309100000_2ae61055-08bc-4dae-9642-2fa90492e264): GRANT ROLE sentry_admin TO GROUP gerardovazquez
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100000_2ae61055-08bc-4dae-9642-2fa90492e264); Time taken: 0.088 seconds
INFO  : OK
No rows affected (0,178 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20170309100000_64ebcc93-c220-4cf9-942d-007a0eed891b): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100000_64ebcc93-c220-4cf9-942d-007a0eed891b); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20170309100000_64ebcc93-c220-4cf9-942d-007a0eed891b): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100000_64ebcc93-c220-4cf9-942d-007a0eed891b); Time taken: 0.129 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0,247 seconds)
```

* more roles and permissions

```sh
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20170309100505_5816ed06-80a1-4e7d-aa3b-b066082faca0): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100505_5816ed06-80a1-4e7d-aa3b-b066082faca0); Time taken: 0.066 seconds
INFO  : Executing command(queryId=hive_20170309100505_5816ed06-80a1-4e7d-aa3b-b066082faca0): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100505_5816ed06-80a1-4e7d-aa3b-b066082faca0); Time taken: 0.043 seconds
INFO  : OK
No rows affected (0,164 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20170309100606_fb3e950d-b455-47b3-9898-61f7f83060ef): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100606_fb3e950d-b455-47b3-9898-61f7f83060ef); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20170309100606_fb3e950d-b455-47b3-9898-61f7f83060ef): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100606_fb3e950d-b455-47b3-9898-61f7f83060ef); Time taken: 0.024 seconds
INFO  : OK
No rows affected (0,087 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> 
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20170309100606_dab214b8-668a-4420-9081-336b67814da1): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100606_dab214b8-668a-4420-9081-336b67814da1); Time taken: 0.069 seconds
INFO  : Executing command(queryId=hive_20170309100606_dab214b8-668a-4420-9081-336b67814da1): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100606_dab214b8-668a-4420-9081-336b67814da1); Time taken: 0.04 seconds
INFO  : OK
No rows affected (0,12 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20170309100606_b1d432d9-e51c-4022-ae3d-102b60cce8e3): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100606_b1d432d9-e51c-4022-ae3d-102b60cce8e3); Time taken: 0.046 seconds
INFO  : Executing command(queryId=hive_20170309100606_b1d432d9-e51c-4022-ae3d-102b60cce8e3): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100606_b1d432d9-e51c-4022-ae3d-102b60cce8e3); Time taken: 0.03 seconds
INFO  : OK
No rows affected (0,084 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> 
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20170309100606_425f5f69-f5ed-4813-913f-d4ca82fd9b57): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100606_425f5f69-f5ed-4813-913f-d4ca82fd9b57); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20170309100606_425f5f69-f5ed-4813-913f-d4ca82fd9b57): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100606_425f5f69-f5ed-4813-913f-d4ca82fd9b57); Time taken: 0.083 seconds
INFO  : OK
No rows affected (0,145 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> 
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20170309100606_5abeaaf8-f9bc-4f75-ba00-bc1a6e9e5de7): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100606_5abeaaf8-f9bc-4f75-ba00-bc1a6e9e5de7); Time taken: 0.049 seconds
INFO  : Executing command(queryId=hive_20170309100606_5abeaaf8-f9bc-4f75-ba00-bc1a6e9e5de7): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100606_5abeaaf8-f9bc-4f75-ba00-bc1a6e9e5de7); Time taken: 0.054 seconds
INFO  : OK
No rows affected (0,115 seconds)
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20170309100606_942f996f-2f89-4803-8702-2a8d1d56a33b): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100606_942f996f-2f89-4803-8702-2a8d1d56a33b); Time taken: 0.049 seconds
INFO  : Executing command(queryId=hive_20170309100606_942f996f-2f89-4803-8702-2a8d1d56a33b): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100606_942f996f-2f89-4803-8702-2a8d1d56a33b); Time taken: 0.052 seconds
INFO  : OK
No rows affected (0,108 seconds)
```

* Test permissions with george

```
beeline> !connect jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM
scan complete in 4ms
Connecting to jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM
Enter username for jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM: george
Enter password for jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.4)
Driver: Hive JDBC (version 1.1.0-cdh5.8.4)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> show tables;
INFO  : Compiling command(queryId=hive_20170309100909_f53ad3df-3ef7-4aab-91c7-a988e0f45ac7): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170309100909_f53ad3df-3ef7-4aab-91c7-a988e0f45ac7); Time taken: 0.077 seconds
INFO  : Executing command(queryId=hive_20170309100909_f53ad3df-3ef7-4aab-91c7-a988e0f45ac7): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309100909_f53ad3df-3ef7-4aab-91c7-a988e0f45ac7); Time taken: 0.155 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0,375 seconds)
```

* Test permissions with ferdinand

```
beeline> !connect jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM
scan complete in 5ms
Connecting to jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM
Enter username for jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM: ferdinand
Enter password for jdbc:hive2://ip-10-0-1-112.eu-west-1.compute.internal:10000/default;principal=hive/ip-10-0-1-112.eu-west-1.compute.internal@EXAMPLE.COM: ********
Connected to: Apache Hive (version 1.1.0-cdh5.8.4)
Driver: Hive JDBC (version 1.1.0-cdh5.8.4)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-10-0-1-112.eu-west-1.compu> show tables;
INFO  : Compiling command(queryId=hive_20170309101111_0b3510f4-913d-4fda-ba32-e3784c085588): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170309101111_0b3510f4-913d-4fda-ba32-e3784c085588); Time taken: 0.068 seconds
INFO  : Executing command(queryId=hive_20170309101111_0b3510f4-913d-4fda-ba32-e3784c085588): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170309101111_0b3510f4-913d-4fda-ba32-e3784c085588); Time taken: 0.164 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0,363 seconds)
```




# Install CM

* List the command and output

```sh
[root@ip-10-0-1-156 ~]# ls /etc/yum.repos.d
CentOS-Base.repo       CentOS-Media.repo  cloudera-manager.repo  epel-testing.repo
CentOS-Debuginfo.repo  CentOS-Vault.repo  epel.repo              mysql-community.repo
```

* Configure Cloudera Manager 

Add to install java and drop scm database first

```sh
[root@ip-10-0-1-156 UnlimitedJCEPolicyJDK8]# /usr/share/cmf/schema/scm_prepare_database.sh mysql -h ip-10-0-1-107.eu-west-1.compute.internal -utemp -ptemp --scm-host ip-10-0-1-156.eu-west-1.compute.internal scm scm '*H4rdPassword#'
JAVA_HOME=/usr/java/jdk1.8.0_121
Verifying that we can write to /etc/cloudera-scm-server
log4j:ERROR Could not find value for key log4j.appender.A
log4j:ERROR Could not instantiate appender named "A".
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_121/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
log4j:ERROR Could not find value for key log4j.appender.A
log4j:ERROR Could not instantiate appender named "A".
[2017-03-10 09:15:18,904] INFO     0[main] - com.cloudera.enterprise.dbutil.DbCommandExecutor.testDbConnection(DbCommandExecutor.java) - Successfully connected to database.
All done, your SCM database is configured correctly!
```





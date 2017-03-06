# MySQL with Replica server

* Install mysql repo

```sh
[root@ip-10-0-1-187 ~]# wget https://dev.mysql.com/get/mysql57-community-release-el6-9.noarch.rpm
[root@ip-10-0-1-187 ~]# yum localinstall mysql57-community-release-el6-9.noarch.rpm -y
Loaded plugins: fastestmirror, presto
Setting up Local Package Process
Examining mysql57-community-release-el6-9.noarch.rpm: mysql57-community-release-el6-9.noarch
Marking mysql57-community-release-el6-9.noarch.rpm to be installed
Loading mirror speeds from cached hostfile
 * base: ftp.heanet.ie
 * epel: s3-mirror-eu-west-1.fedoraproject.org
 * extras: ftp.heanet.ie
 * updates: ftp.heanet.ie
Resolving Dependencies
--> Running transaction check
---> Package mysql57-community-release.noarch 0:el6-9 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================
 Package                               Arch               Version             Repository                                           Size
========================================================================================================================================
Installing:
 mysql57-community-release             noarch             el6-9               /mysql57-community-release-el6-9.noarch             8.6 k

Transaction Summary
========================================================================================================================================
Install       1 Package(s)

Total size: 8.6 k
Installed size: 8.6 k
Downloading Packages:
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : mysql57-community-release-el6-9.noarch                                                                               1/1 
  Verifying  : mysql57-community-release-el6-9.noarch                                                                               1/1 

Installed:
  mysql57-community-release.noarch 0:el6-9                                                                                              

Complete!

```

* edit repo to enable mysql 5.5 and disable 5.7

* install mysql package

```sh
[root@ip-10-0-1-187 ~]# yum install mysql
Loaded plugins: fastestmirror, presto
Setting up Install Process
Loading mirror speeds from cached hostfile
 * base: ftp.heanet.ie
 * epel: s3-mirror-eu-west-1.fedoraproject.org
 * extras: ftp.heanet.ie
 * updates: ftp.heanet.ie
mysql-connectors-community                                                                                       | 2.5 kB     00:00     
mysql-connectors-community/primary_db                                                                            |  13 kB     00:00     
mysql-tools-community                                                                                            | 2.5 kB     00:00     
mysql-tools-community/primary_db                                                                                 |  34 kB     00:00     
mysql55-community                                                                                                | 2.5 kB     00:00     
mysql55-community/primary_db                                                                                     | 162 kB     00:00     
Package mysql is obsoleted by mysql-community-client, trying to install mysql-community-client-5.5.54-2.el6.x86_64 instead
Resolving Dependencies
--> Running transaction check
---> Package mysql-community-client.x86_64 0:5.5.54-2.el6 will be installed
--> Processing Dependency: mysql-community-libs(x86-64) >= 5.5.8 for package: mysql-community-client-5.5.54-2.el6.x86_64
--> Running transaction check
---> Package mysql-community-libs.x86_64 0:5.5.54-2.el6 will be obsoleting
--> Processing Dependency: mysql-community-common(x86-64) >= 5.5.8 for package: mysql-community-libs-5.5.54-2.el6.x86_64
---> Package mysql-libs.x86_64 0:5.1.73-8.el6_8 will be obsoleted
--> Processing Dependency: libmysqlclient.so.16()(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Processing Dependency: libmysqlclient.so.16(libmysqlclient_16)(64bit) for package: 2:postfix-2.6.6-6.el6_7.1.x86_64
--> Running transaction check
---> Package mysql-community-common.x86_64 0:5.5.54-2.el6 will be installed
---> Package mysql-community-libs-compat.x86_64 0:5.5.54-2.el6 will be obsoleting
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================
 Package                                    Arch                  Version                        Repository                        Size
========================================================================================================================================
Installing:
 mysql-community-client                     x86_64                5.5.54-2.el6                   mysql55-community                 15 M
 mysql-community-libs                       x86_64                5.5.54-2.el6                   mysql55-community                1.7 M
     replacing  mysql-libs.x86_64 5.1.73-8.el6_8
 mysql-community-libs-compat                x86_64                5.5.54-2.el6                   mysql55-community                1.6 M
     replacing  mysql-libs.x86_64 5.1.73-8.el6_8
Installing for dependencies:
 mysql-community-common                     x86_64                5.5.54-2.el6                   mysql55-community                277 k

Transaction Summary
========================================================================================================================================
Install       4 Package(s)

Total download size: 18 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 18 M
(1/4): mysql-community-client-5.5.54-2.el6.x86_64.rpm                                                            |  15 MB     00:00     
(2/4): mysql-community-common-5.5.54-2.el6.x86_64.rpm                                                            | 277 kB     00:00     
(3/4): mysql-community-libs-5.5.54-2.el6.x86_64.rpm                                                              | 1.7 MB     00:00     
(4/4): mysql-community-libs-compat-5.5.54-2.el6.x86_64.rpm                                                       | 1.6 MB     00:00     
----------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                    24 MB/s |  18 MB     00:00     
warning: rpmts_HdrFromFdno: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Importing GPG key 0x5072E1F5:
 Userid : MySQL Release Engineering <mysql-build@oss.oracle.com>
 Package: mysql57-community-release-el6-9.noarch (@/mysql57-community-release-el6-9.noarch)
 From   : /etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Is this ok [y/N]: y
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : mysql-community-common-5.5.54-2.el6.x86_64                                                                           1/5 
  Installing : mysql-community-libs-5.5.54-2.el6.x86_64                                                                             2/5 
  Installing : mysql-community-client-5.5.54-2.el6.x86_64                                                                           3/5 
  Installing : mysql-community-libs-compat-5.5.54-2.el6.x86_64                                                                      4/5 
  Erasing    : mysql-libs-5.1.73-8.el6_8.x86_64                                                                                     5/5 
  Verifying  : mysql-community-common-5.5.54-2.el6.x86_64                                                                           1/5 
  Verifying  : mysql-community-libs-5.5.54-2.el6.x86_64                                                                             2/5 
  Verifying  : mysql-community-client-5.5.54-2.el6.x86_64                                                                           3/5 
  Verifying  : mysql-community-libs-compat-5.5.54-2.el6.x86_64                                                                      4/5 
  Verifying  : mysql-libs-5.1.73-8.el6_8.x86_64                                                                                     5/5 

Installed:
  mysql-community-client.x86_64 0:5.5.54-2.el6                           mysql-community-libs.x86_64 0:5.5.54-2.el6                     
  mysql-community-libs-compat.x86_64 0:5.5.54-2.el6                     

Dependency Installed:
  mysql-community-common.x86_64 0:5.5.54-2.el6                                                                                          

Replaced:
  mysql-libs.x86_64 0:5.1.73-8.el6_8                                                                                                    

Complete!
```

* install jdbc connector in all hosts

```sh
[root@ip-10-0-1-187 ~]# wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.41.tar.gz
[root@ip-10-0-1-187 ~]# tar -xvzf mysql-connector-java-5.1.41.tar.gz
```

* install mysql-server on master and slave

Master will be cloudera01 and Slave will be cloudera02

```sh
[root@ip-10-0-1-128 ~]# yum install mysql-server
[root@ip-10-0-1-128 ~]# chkconfig mysqld on
[root@ip-10-0-1-128 ~]# service mysqld start
Initializing MySQL database:  170306 16:05:16 [Note] Ignoring --secure-file-priv value as server is running with --bootstrap.
170306 16:05:16 [Note] /usr/sbin/mysqld (mysqld 5.5.54) starting as process 1449 ...
170306 16:05:16 [Note] Ignoring --secure-file-priv value as server is running with --bootstrap.
170306 16:05:16 [Note] /usr/sbin/mysqld (mysqld 5.5.54) starting as process 1456 ...

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:

/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h ip-10-0-1-177 password 'new-password'

Alternatively you can run:
/usr/bin/mysql_secure_installation

which will also give you the option of removing the test
databases and anonymous user created by default.  This is
strongly recommended for production servers.

See the manual for more instructions.

Please report any problems at http://bugs.mysql.com/

                                                           [  OK  ]
Starting mysqld:                                           [  OK  ]

[root@ip-10-0-1-128 ~]# /usr/bin/mysql_secure_installation




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] y
 ... Success!

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!

[root@ip-10-0-1-128 ~]# service mysqld stop
Stopping mysqld:                                           [  OK  ]

[root@ip-10-0-1-128 ~]# ls /var/lib/mysql
ibdata1  ib_logfile0  ib_logfile1  mysql  performance_schema

[root@ip-10-0-1-128 mysql]# mkdir /root/mysql-bkp/; cd /var/lib/mysql
[root@ip-10-0-1-128 mysql]# mv ib_logfile* /root/mysql-bkp/.
```

* Edit /etc/mysql.cnf to prepare for replication [add log and server-id]

```sh
[mysqld]
server-id = 2
transaction-isolation = READ-COMMITTED
# Disabling symbolic-links is recommended to prevent assorted security risks;
# to do so, uncomment this line:
# symbolic-links = 0

key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1

max_connections = 550

#expire_logs_days = 10
#max_binlog_size = 100M

datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock

#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
log_bin=/var/lib/mysql/mysql_binary_log
log-bin=mysql-bin

# For MySQL version 5.1.8 or later. For older versions, reference MySQL documentation for configuration help.
binlog_format = mixed

read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M

# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

sql_mode=STRICT_ALL_TABLES
```

* create log folder on both machines

```sh
[root@ip-10-0-1-177 ~]# mkdir -p /var/lib/mysql/mysql_binary_log
[root@ip-10-0-1-177 ~]# chown mysql:mysql /var/lib/mysql/mysql_binary_log
```

* setup replication on Master ip-10-0-1-128.eu-west-1.compute.internal

```sh
[root@ip-10-0-1-128 ~] mysql -p -u root 
mysql> create user replicant@'ip-10-0-1-177.eu-west-1.compute.internal' identified by '*SecretReplicant#';
mysql> GRANT REPLICATION SLAVE ON *.* TO 'replicant'@'ip-10-0-1-177.eu-west-1.compute.internal';
mysql> Flush Privileges; 
mysql> SET GLOBAL binlog_format = 'ROW'; 
mysql> FLUSH TABLES WITH READ LOCK;
mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000002 |      586 |              |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)
```

* setup replication on Slave ip-10-0-1-177.eu-west-1.compute.internal

```sh
mysql> CHANGE MASTER TO MASTER_HOST='ip-10-0-1-128.eu-west-1.compute.internal', MASTER_USER='replicant', MASTER_PASSWORD='*SecretReplicant#', MASTER_LOG_FILE='mysql-bin.000002', MASTER_LOG_POS=586;
mysql> START SLAVE;
mysql> SHOW SLAVE STATUS \G
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: ip-10-0-1-128.eu-west-1.compute.internal
                  Master_User: replicant
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000002
          Read_Master_Log_Pos: 586
               Relay_Log_File: mysqld-relay-bin.000002
                Relay_Log_Pos: 253
        Relay_Master_Log_File: mysql-bin.000002
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB: 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 0
                   Last_Error: 
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 586
              Relay_Log_Space: 410
              Until_Condition: None
               Until_Log_File: 
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error: 
               Last_SQL_Errno: 0
               Last_SQL_Error: 
  Replicate_Ignore_Server_Ids: 
             Master_Server_Id: 1
1 row in set (0.00 sec)
```
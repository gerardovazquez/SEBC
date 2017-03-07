# Pre-Install

## Install extra software and update

```sh
[root@ip-10-0-1-187 ~]# yum install epel-release -y
[root@ip-10-0-1-187 ~]# yum install ntp sudo wget git bind-utils unzip -y
[root@ip-10-0-1-187 ~]# yum update -y #(my bad.. upgraded to 6.8!)
[root@ip-10-0-1-187 ~]# reboot
```

##  vm.swappiness

* check vm.swappiness

```sh
[root@ip-10-0-1-187 ~]# cat /proc/sys/vm/swappiness
60
```

* check kernel version

```sh
[root@ip-10-0-1-187 ~]# uname -r
2.6.32-431.el6.x86_64
```

* set vm.swappiness

```sh
sysctl -w vm.swappiness=1
echo "vm.swappiness=1" > /etc/sysctl.conf
```

* check again

```sh
[root@ip-10-0-1-187 ~]# cat /proc/sys/vm/swappiness 
1
```

## check system settings

* download check script and run it

```sh
[root@ip-10-0-1-187 ~]# wget https://raw.githubusercontent.com/gerardovazquez/SEBC/master/installation/tools/script.sh
[root@ip-10-0-1-187 ~]# chmod a+x script.sh
[root@ip-10-0-1-187 ~]# ./script.sh $(hostname -i) $(hostname -f)

The Report about the System's Swappiness, IP tables, name resolution and no. of cores in the system
___________________________________________________________________________________________________

The current swappiness of the system is 
1

************************************************

The hostname for a given IP address
ip-10-0-1-187.eu-west-1.compute.internal.

************************************************

The IP address for a given hostname is
10.0.1.187
************************************************

The current status of the IP tables service is 
Table: filter
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
2    ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
3    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:22 
5    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited 

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         
1    REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-host-prohibited 

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         


************************************************

To test if the Firewall software status (on/off)
iptables       	0:off	1:off	2:on	3:on	4:on	5:on	6:off

Now for IPv6
ip6tables      	0:off	1:off	2:on	3:on	4:on	5:on	6:off

************************************************

The number of cores available in the system are 
4
```

Iptables are enabled but accepting all traffic
Disabling Iptables
```sh
[root@ip-10-0-1-187 ~]# chkconfig iptables off
[root@ip-10-0-1-187 ~]# chkconfig ip6tables off
[root@ip-10-0-1-187 ~]# service iptables stop
iptables: Setting chains to policy ACCEPT: filter          [  OK  ]
iptables: Flushing firewall rules:                         [  OK  ]
iptables: Unloading modules:                               [  OK  ]
[root@ip-10-0-1-187 ~]# service ip6tables stop
ip6tables: Setting chains to policy ACCEPT: filter         [  OK  ]
ip6tables: Flushing firewall rules:                        [  OK  ]
ip6tables: Unloading modules:                              [  OK  ]
```

## check SELinux

```sh
[root@ip-10-0-1-187 ~]# getenforce 
Enforcing
```

## Add data volume

Data volume has been created in AWS console and attached to each machine

* create partition

```sh
[root@ip-10-0-1-187 ~]# echo -e "o\nn\np\n1\n\n\nw" | fdisk /dev/xvdj
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x48eb29da.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): Building a new DOS disklabel with disk identifier 0x01f6e149.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): Command action
   e   extended
   p   primary partition (1-4)
Partition number (1-4): First cylinder (1-13054, default 1): Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-13054, default 13054): Using default value 13054

Command (m for help): The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

[root@ip-10-0-1-187 ~]# fdisk -l

Disk /dev/xvde: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/xvdj: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01f6e149

    Device Boot      Start         End      Blocks   Id  System
/dev/xvdj1               1       13054   104856223+  83  Linux
```

* format partition

```sh
[root@ip-10-0-1-187 ~]# mkfs.ext4 /dev/xvdj1
```

* add to fstab

```sh
[root@ip-10-0-1-187 ~]# mkdir -p /data/01
[root@ip-10-0-1-187 ~]# echo '/dev/xvdj1              /data/01        ext4      defaults,noatime         0 0'  >> /etc/fstab
[root@ip-10-0-1-187 ~]# mount /data/01
```


## Show the mount attributes of all volumes

```sh
[root@ip-10-0-1-187 ~]# mount 
/dev/xvde on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/xvdj1 on /data/01 type ext4 (rw,noatime)

```

## Show the reserve space of any non-root, ext-based volumes 

```sh
[root@ip-10-0-1-187 ~]# tune2fs -l /dev/xvdj1 
tune2fs 1.41.12 (17-May-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          d6ebe98c-4d8b-40ce-8c11-2a93ed1352fe
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6553600
Block count:              26214055
Reserved block count:     1310702
Free blocks:              25754706
Free inodes:              6553589
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Mon Mar  6 14:41:11 2017
Last mount time:          Mon Mar  6 15:08:36 2017
Last write time:          Mon Mar  6 15:08:36 2017
Mount count:              1
Maximum mount count:      26
Last checked:             Mon Mar  6 14:41:11 2017
Check interval:           15552000 (6 months)
Next check after:         Sat Sep  2 14:41:11 2017
Lifetime writes:          1733 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      0ed2a9a7-5fdb-40db-b10b-2ab262076aed
Journal backup:           inode blocks

```

* free reserved space

```sh
[root@ip-10-0-1-187 ~]# tune2fs -m0 /dev/xvdj1 
tune2fs 1.41.12 (17-May-2010)
Setting reserved blocks percentage to 0% (0 blocks)
```


## Disable transparent hugepage support

```sh
[root@ip-10-0-1-187 ~]# ls -l /sys/kernel/mm/
total 0
drwxr-xr-x. 3 root root 0 2017-03-06 14:56 hugepages
drwxr-xr-x. 2 root root 0 2017-03-06 14:56 ksm
```
THP seems to be not present in this version Centos 6.5 wuth kernel 2.6.32
We create a disable THP script just in case in /etc/init.d/disable-thp


```sh
#!/bin/bash
### BEGIN INIT INFO
# Provides: disable-thp
# Required-Start: $local_fs
# Required-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Disable THP
# Description: disables Transparent Huge Pages (THP) on boot
### END INIT INFO

 
case $1 in
  start)
    if [ -d /sys/kernel/mm/transparent_hugepage ]; then
       echo 'never' > /sys/kernel/mm/transparent_hugepage/enabled
       echo 'never' > /sys/kernel/mm/transparent_hugepage/defrag
    elif [ -d /sys/kernel/mm/redhat_transparent_hugepage ]; then
      echo 'never' > /sys/kernel/mm/redhat_transparent_hugepage/enabled
      echo 'never' > /sys/kernel/mm/redhat_transparent_hugepage/defrag
   else
      return 0
   fi
   ;;
esac
```

```sh
[root@ip-10-0-1-187 ~]# chmod a+x /etc/init.d/disable-thp 
[root@ip-10-0-1-187 ~]# chkconfig disable-thp on
```

## List your network interface configuration

```sh
[root@ip-10-0-1-187 ~]# ifconfig
eth0      Link encap:Ethernet  HWaddr 06:F5:B1:92:D4:DF  
          inet addr:10.0.1.187  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4f5:b1ff:fe92:d4df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74261 (72.5 KiB)  TX bytes:112492 (109.8 KiB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

## List forward and reverse host lookups using getent or nslookup

```sh
[root@ip-10-0-1-187 ~]# nslookup ip-10-0-1-187
Server:		10.0.0.2
Address:	10.0.0.2#53

Non-authoritative answer:
Name:	ip-10-0-1-187.eu-west-1.compute.internal
Address: 10.0.1.187

[root@ip-10-0-1-187 ~]# nslookup 10.0.1.187
Server:		10.0.0.2
Address:	10.0.0.2#53

Non-authoritative answer:
187.1.0.10.in-addr.arpa	name = ip-10-0-1-187.eu-west-1.compute.internal.

Authoritative answers can be found from:

```

## Show the nscd service is running

```sh
[root@ip-10-0-1-187 ~]# service nscd status
nscd: unrecognized service
[root@ip-10-0-1-187 ~]# yum install nscd -y
Loaded plugins: fastestmirror, presto
Setting up Install Process
Loading mirror speeds from cached hostfile
 * base: ftp.heanet.ie
 * epel: s3-mirror-eu-west-1.fedoraproject.org
 * extras: ftp.heanet.ie
 * updates: ftp.heanet.ie
Resolving Dependencies
--> Running transaction check
---> Package nscd.x86_64 0:2.12-1.192.el6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================
 Package                      Arch                           Version                                 Repository                    Size
========================================================================================================================================
Installing:
 nscd                         x86_64                         2.12-1.192.el6                          base                         230 k

Transaction Summary
========================================================================================================================================
Install       1 Package(s)

Total download size: 230 k
Installed size: 180 k
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 230 k
nscd-2.12-1.192.el6.x86_64.rpm                                                                                   | 230 kB     00:00     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : nscd-2.12-1.192.el6.x86_64                                                                                           1/1 
  Verifying  : nscd-2.12-1.192.el6.x86_64                                                                                           1/1 

Installed:
  nscd.x86_64 0:2.12-1.192.el6                                                                                                          

Complete!
[root@ip-10-0-1-187 ~]# chkconfig nscd on
[root@ip-10-0-1-187 ~]# service nscd start
Starting nscd:                                             [  OK  ]
[root@ip-10-0-1-187 ~]# service nscd status
nscd (pid 1200) is running...
```


## Show the ntpd service is running

We did previously install it on the first step

```sh
[root@ip-10-0-1-187 ~]# service ntpd status
ntpd is stopped
[root@ip-10-0-1-187 ~]# service ntpd start
Starting ntpd:                                             [  OK  ]
[root@ip-10-0-1-187 ~]# service ntpd status
ntpd (pid  1259) is running...

```

## MySQL Server installation and configuration in in 2_replica_working.md

## Install ClouderaManager

* setup JDK 1.8u121 + JCE 

```sh
[root@ip-10-0-1-187 ~]#  wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.rpm"
[root@ip-10-0-1-187 ~]# yum localinstall jdk-8u121-linux-x64.rpm -y
[root@ip-10-0-1-187 ~]# wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip"
[root@ip-10-0-1-187 ~]# unzip *.zip
Archive:  jce_policy-8.zip
   creating: UnlimitedJCEPolicyJDK8/
  inflating: UnlimitedJCEPolicyJDK8/local_policy.jar  
  inflating: UnlimitedJCEPolicyJDK8/README.txt  
  inflating: UnlimitedJCEPolicyJDK8/US_export_policy.jar  
[root@ip-10-0-1-187 UnlimitedJCEPolicyJDK8]# cp *.jar /usr/java/jdk1.8.0_121/jre/lib/security/.
cp: overwrite `/usr/java/jdk1.8.0_121/jre/lib/security/./local_policy.jar'? y
cp: overwrite `/usr/java/jdk1.8.0_121/jre/lib/security/./US_export_policy.jar'? y
[root@ip-10-0-1-187 ~]# cp mysql-connector-java-5.1.41/mysql-connector-java-5.1.41-bin.jar /usr/share/java/mysql-connector-java.jar
```

* setup cloudera manager repo

```sh
[root@ip-10-0-1-187 ~]# wget https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/cloudera-manager.repo?_ga=1.243758661.1732162428.1467798696 -O /etc/yum.repos.d/cm.repo
```

* install Cloudera Manager

  Re-installation with right version (5.8.3)

```sh
[root@ip-10-0-1-128 ~]# yum install cloudera-manager-daemons cloudera-manager-server
Loaded plugins: fastestmirror, presto
Setting up Install Process
Determining fastest mirrors
epel/metalink                                                                                                    |  24 kB     00:00     
 * base: ftp.heanet.ie
 * epel: mirror.freethought-internet.co.uk
 * extras: ftp.heanet.ie
 * updates: ftp.heanet.ie
base                                                                                                             | 3.7 kB     00:00     
base/primary_db                                                                                                  | 4.7 MB     00:00     
cloudera-manager                                                                                                 |  951 B     00:00     
cloudera-manager/primary                                                                                         | 4.3 kB     00:00     
cloudera-manager                                                                                                                    7/7
epel                                                                                                             | 4.3 kB     00:00     
epel/primary_db                                                                                                  | 5.9 MB     00:00     
extras                                                                                                           | 3.4 kB     00:00     
extras/primary_db                                                                                                |  37 kB     00:00     
mysql-connectors-community                                                                                       | 2.5 kB     00:00     
mysql-connectors-community/primary_db                                                                            |  13 kB     00:00     
mysql-tools-community                                                                                            | 2.5 kB     00:00     
mysql-tools-community/primary_db                                                                                 |  34 kB     00:00     
mysql55-community                                                                                                | 2.5 kB     00:00     
mysql55-community/primary_db                                                                                     | 162 kB     00:00     
updates                                                                                                          | 3.4 kB     00:00     
updates/primary_db                                                                                               | 5.4 MB     00:00     
Resolving Dependencies
--> Running transaction check
---> Package cloudera-manager-daemons.x86_64 0:5.8.3-1.cm583.p0.8.el6 will be installed
---> Package cloudera-manager-server.x86_64 0:5.8.3-1.cm583.p0.8.el6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================
 Package                                Arch                 Version                               Repository                      Size
========================================================================================================================================
Installing:
 cloudera-manager-daemons               x86_64               5.8.3-1.cm583.p0.8.el6                cloudera-manager               529 M
 cloudera-manager-server                x86_64               5.8.3-1.cm583.p0.8.el6                cloudera-manager               8.2 k

Transaction Summary
========================================================================================================================================
Install       2 Package(s)

Total download size: 529 M
Installed size: 678 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 529 M
(1/2): cloudera-manager-daemons-5.8.3-1.cm583.p0.8.el6.x86_64.rpm                                                | 529 MB     00:18     
(2/2): cloudera-manager-server-5.8.3-1.cm583.p0.8.el6.x86_64.rpm                                                 | 8.2 kB     00:00     
----------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                    29 MB/s | 529 MB     00:18     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : cloudera-manager-daemons-5.8.3-1.cm583.p0.8.el6.x86_64                                                               1/2 
  Installing : cloudera-manager-server-5.8.3-1.cm583.p0.8.el6.x86_64                                                                2/2 
  Verifying  : cloudera-manager-server-5.8.3-1.cm583.p0.8.el6.x86_64                                                                1/2 
  Verifying  : cloudera-manager-daemons-5.8.3-1.cm583.p0.8.el6.x86_64                                                               2/2 

Installed:
  cloudera-manager-daemons.x86_64 0:5.8.3-1.cm583.p0.8.el6            cloudera-manager-server.x86_64 0:5.8.3-1.cm583.p0.8.el6           

Complete!
```

* start cloudera manager

```sh
[root@ip-10-0-1-128 ~]# service cloudera-scm-server start
Starting cloudera-scm-server:                              [  OK  ]
```
Fails because database has not been created.

* create needed databases

Using the mysql console

```sh
mysql> create database amon DEFAULT CHARACTER SET utf8;
mysql> grant all on amon.* TO 'amon'@'%' IDENTIFIED BY '*H4rdPassword#';

mysql> create database rman DEFAULT CHARACTER SET utf8;
mysql> grant all on rman.* TO 'rman'@'%' IDENTIFIED BY '*H4rdPassword#';

mysql> create database metastore DEFAULT CHARACTER SET utf8;
mysql> grant all on metastore.* TO 'hive'@'%' IDENTIFIED BY '*H4rdPassword#';

mysql> create database sentry DEFAULT CHARACTER SET utf8;
mysql> grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY '*H4rdPassword#';

mysql> create database nav DEFAULT CHARACTER SET utf8;
mysql> grant all on nav.* TO 'nav'@'%' IDENTIFIED BY '*H4rdPassword#';

mysql> create database navms DEFAULT CHARACTER SET utf8;
mysql> grant all on navms.* TO 'navms'@'%' IDENTIFIED BY '*H4rdPassword#';

mysql> create database hue;
mysql> grant all on hue.* to 'hue'@'%' identified by '*H4rdPassword#';

mysql> create database oozie;
mysql> grant all privileges on oozie.* to 'oozie'@'%' identified by '*H4rdPassword#';
```

Using the setup tool for CM database

```sh
mysql> grant all on *.* to 'temp'@'%' identified by 'temp' with grant option;
```

```sh
[root@ip-10-0-1-128 ~]# /usr/share/cmf/schema/scm_prepare_database.sh mysql -h ip-10-0-1-128.eu-west-1.compute.internal -utemp -ptemp --scm-host ip-10-0-1-128.eu-west-1.compute.internal scm scm '*H4rdPassword#'
JAVA_HOME=/usr/java/jdk1.8.0_121
Verifying that we can write to /etc/cloudera-scm-server
log4j:ERROR Could not find value for key log4j.appender.A
log4j:ERROR Could not instantiate appender named "A".
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_121/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
log4j:ERROR Could not find value for key log4j.appender.A
log4j:ERROR Could not instantiate appender named "A".
[2017-03-06 23:16:03,933] INFO     0[main] - com.cloudera.enterprise.dbutil.DbCommandExecutor.testDbConnection(DbCommandExecutor.java) - Successfully connected to database.
All done, your SCM database is configured correctly!
```

```sh
mysql> drop user 'temp'@'%';
```

```sh
[root@ip-10-0-1-128 ~]# service cloudera-scm-server start
Starting cloudera-scm-server:                              [  OK  ]
[root@ip-10-0-1-128 ~]# service cloudera-scm-server status
cloudera-scm-server (pid  5931) is running...
```

## install following the wizard

* Use options defined in installation.md

* Fix root partition size problem

```sh
[root@ip-10-0-1-128 ~]# resize2fs /dev/xvde 
resize2fs 1.41.12 (17-May-2010)
Filesystem at /dev/xvde is mounted on /; on-line resizing required
old desc_blocks = 1, new_desc_blocks = 7
Performing an on-line resize of /dev/xvde to 26214400 (4k) blocks.
The filesystem on /dev/xvde is now 26214400 blocks long.
```


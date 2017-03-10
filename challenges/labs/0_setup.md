# Challenge Setup


*    List the cloud provider you are using (AWS, GCE, Azure, other)
AWS

*    List the nodes you are using by IP address and name
34.249.130.59  ec2-34-249-130-59.eu-west-1.compute.amazonaws.com   ip-10-0-1-107.eu-west-1.compute.internal 
34.251.138.92  ec2-34-251-138-92.eu-west-1.compute.amazonaws.com   ip-10-0-1-156.eu-west-1.compute.internal 
34.251.183.175 ec2-34-251-183-175.eu-west-1.compute.amazonaws.com  ip-10-0-1-204.eu-west-1.compute.internal 
34.252.109.5   ec2-34-252-109-5.eu-west-1.compute.amazonaws.com    ip-10-0-1-179.eu-west-1.compute.internal
34.252.64.40   ec2-34-252-64-40.eu-west-1.compute.amazonaws.com    ip-10-0-1-78.eu-west-1.compute.internal

*    List the Linux release you are using
```sh
[root@ip-10-0-1-107 ~]# cat /etc/redhat-release 
CentOS release 6.5 (Final)
```

*    Demonstrate the disk capacity available on each node is >= 30 GB

```sh
[root@ip-10-0-1-107 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde        99G  840M   93G   1% /
tmpfs           7,4G     0  7,4G   0% /dev/shm
/dev/xvdk1       99G  188M   99G   1% /data/01
/dev/xvdj1       99G  188M   99G   1% /data/02
```


*    List the command and output for yum repolist enabled
```sh
[root@ip-10-0-1-107 ~]# yum repolist
Loaded plugins: fastestmirror, presto
base                                                                                                             | 3.7 kB     00:00     
base/primary_db                                                                                                  | 4.7 MB     00:00     
extras                                                                                                           | 3.4 kB     00:00     
extras/primary_db                                                                                                |  37 kB     00:00     
updates                                                                                                          | 3.4 kB     00:00     
updates/primary_db                                                                                               | 5.4 MB     00:00     
repo id                                                    repo name                                                              status
base                                                       CentOS-6 - Base                                                        6.696
extras                                                     CentOS-6 - Extras                                                         64
updates                                                    CentOS-6 - Updates                                                       959
repolist: 7.719
```

* Add the following Linux accounts to all nodes 

```sh
[root@ip-10-0-1-107 ~]# adduser -u 2010 neymar 
[root@ip-10-0-1-107 ~]# adduser -u 2016 ronaldo 
[root@ip-10-0-1-107 ~]# groupadd barca
[root@ip-10-0-1-107 ~]# groupadd merengues
[root@ip-10-0-1-107 ~]# usermod -a -G barca ronaldo
[root@ip-10-0-1-107 ~]# usermod -a -G merengues neymar
```

* List the /etc/passwd entries for neymar and ronaldo 

```sh
[root@ip-10-0-1-107 ~]# grep -E "^ronaldo.*|^neymar.*" /etc/passwd
neymar:x:2010:2010::/home/neymar:/bin/bash
ronaldo:x:2016:2016::/home/ronaldo:/bin/bash
```

* List the /etc/group entries for barca and merengues

```sh
[root@ip-10-0-1-107 ~]# grep -E "^merengues.*|^barca.*" /etc/group
barca:x:2017:ronaldo
merengues:x:2018:neymar
```

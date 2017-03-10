# Setup MySQL

* The hostname of your db server node

```sh
[root@ip-10-0-1-107 ~]# hostname -f
ip-10-0-1-107.eu-west-1.compute.internal
```

* The command and output for display your database server's version

```sh
[root@ip-10-0-1-107 ~]# mysql --version
mysql  Ver 14.14 Distrib 5.6.35, for Linux (x86_64) using  EditLine wrapper
```

* The command and output for listing your created databases

```sh
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0,00 sec)
```
* Teragen Neymar

```sh
[neymar@ip-10-0-1-107 ~]$ kinit neymar
Password for neymar@GERARDOVAZQUEZ.ES: 
[neymar@ip-10-0-1-107 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort -Dmapreduce.job.maps=8 -Dmapreduce.job.reduces=8 tgen640 tsort640m 1>terasort.out 2>terasort.err
```

```sh

```
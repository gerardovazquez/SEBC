# Test HDFS performance

## Create an end-user Linux account named with your GitHub handle 

Already done in replciation

## Create a 10 GB file using teragen 

```sh
[gerardovazquez@ip-10-0-1-177 ~]$ time hadoop jar  /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapred.map.tasks=4 -Dmapred.map.tasks.speculative.execution=false -Ddfs.blocksize=32m 107374183 /user/gerardovazquez/performance
real	2m52.049s
user	0m7.058s
sys	0m0.940s

[gerardovazquez@ip-10-0-1-177 ~]$ hdfs dfs -ls -h /user/gerardovazquez/performance
Found 5 items
-rw-r--r--   3 gerardovazquez gerardovazquez          0 2017-03-07 12:22 /user/gerardovazquez/performance/_SUCCESS
-rw-r--r--   3 gerardovazquez gerardovazquez      2.5 G 2017-03-07 12:22 /user/gerardovazquez/performance/part-m-00000
-rw-r--r--   3 gerardovazquez gerardovazquez      2.5 G 2017-03-07 12:22 /user/gerardovazquez/performance/part-m-00001
-rw-r--r--   3 gerardovazquez gerardovazquez      2.5 G 2017-03-07 12:22 /user/gerardovazquez/performance/part-m-00002
-rw-r--r--   3 gerardovazquez gerardovazquez      2.5 G 2017-03-07 12:22 /user/gerardovazquez/performance/part-m-00003
[gerardovazquez@ip-10-0-1-177 ~]$ hdfs fsck /user/gerardovazquez/performance -files
Connecting to namenode via http://ip-10-0-1-112.eu-west-1.compute.internal:50070
FSCK started by gerardovazquez (auth:SIMPLE) from /10.0.1.177 for path /user/gerardovazquez/performance at Tue Mar 07 12:25:29 UTC 2017
/user/gerardovazquez/performance <dir>
/user/gerardovazquez/performance/_SUCCESS 0 bytes, 0 block(s):  OK
/user/gerardovazquez/performance/part-m-00000 2684354600 bytes, 81 block(s):  OK
/user/gerardovazquez/performance/part-m-00001 2684354600 bytes, 81 block(s):  OK
/user/gerardovazquez/performance/part-m-00002 2684354600 bytes, 81 block(s):  OK
/user/gerardovazquez/performance/part-m-00003 2684354500 bytes, 80 block(s):  OK
Status: HEALTHY
 Total size:	10737418300 B
 Total dirs:	1
 Total files:	5
 Total symlinks:		0
 Total blocks (validated):	323 (avg. block size 33242781 B)
 Minimally replicated blocks:	323 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue Mar 07 12:25:29 UTC 2017 in 3 milliseconds


The filesystem under path '/user/gerardovazquez/performance' is HEALTHY
```

## run terasort

```sh
[gerardovazquez@ip-10-0-1-177 ~]$ time hadoop  jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort  -Dmapred.reduce.tasks=12 -Dmapred.reduce.tasks.speculative.execution=false -Dmapreduce.task.io.sort.factor=1000 performance terasort-output
real	7m52.625s
user	0m9.666s
sys	0m1.225s
```



# Test HDFS

* The full teragen command and job output 

```sh 
[neymar@ip-10-0-1-107 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapreduce.job.maps=8 -Ddfs.blockSize=16m 65536000 tgen640 1>teragen.out 2>teragen.err
```
```
17/03/10 10:15:06 INFO client.RMProxy: Connecting to ResourceManager at ip-10-0-1-107.eu-west-1.compute.internal/10.0.1.107:8032
17/03/10 10:15:06 INFO terasort.TeraSort: Generating 65536000 using 8
17/03/10 10:15:06 INFO mapreduce.JobSubmitter: number of splits:8
17/03/10 10:15:07 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1489140033717_0002
17/03/10 10:15:07 INFO impl.YarnClientImpl: Submitted application application_1489140033717_0002
17/03/10 10:15:07 INFO mapreduce.Job: The url to track the job: http://ip-10-0-1-107.eu-west-1.compute.internal:8088/proxy/application_1489140033717_0002/
17/03/10 10:15:07 INFO mapreduce.Job: Running job: job_1489140033717_0002
17/03/10 10:15:13 INFO mapreduce.Job: Job job_1489140033717_0002 running in uber mode : false
17/03/10 10:15:13 INFO mapreduce.Job:  map 0% reduce 0%
17/03/10 10:15:25 INFO mapreduce.Job:  map 6% reduce 0%
17/03/10 10:15:26 INFO mapreduce.Job:  map 8% reduce 0%
17/03/10 10:15:27 INFO mapreduce.Job:  map 14% reduce 0%
17/03/10 10:15:28 INFO mapreduce.Job:  map 20% reduce 0%
17/03/10 10:15:30 INFO mapreduce.Job:  map 22% reduce 0%
17/03/10 10:15:31 INFO mapreduce.Job:  map 23% reduce 0%
17/03/10 10:15:32 INFO mapreduce.Job:  map 24% reduce 0%
17/03/10 10:15:33 INFO mapreduce.Job:  map 26% reduce 0%
17/03/10 10:15:34 INFO mapreduce.Job:  map 27% reduce 0%
17/03/10 10:15:43 INFO mapreduce.Job:  map 31% reduce 0%
17/03/10 10:15:46 INFO mapreduce.Job:  map 34% reduce 0%
17/03/10 10:15:47 INFO mapreduce.Job:  map 35% reduce 0%
17/03/10 10:15:49 INFO mapreduce.Job:  map 37% reduce 0%
17/03/10 10:15:50 INFO mapreduce.Job:  map 40% reduce 0%
17/03/10 10:15:53 INFO mapreduce.Job:  map 41% reduce 0%
17/03/10 10:15:58 INFO mapreduce.Job:  map 48% reduce 0%
17/03/10 10:16:01 INFO mapreduce.Job:  map 53% reduce 0%
17/03/10 10:16:04 INFO mapreduce.Job:  map 57% reduce 0%
17/03/10 10:16:07 INFO mapreduce.Job:  map 58% reduce 0%
17/03/10 10:16:13 INFO mapreduce.Job:  map 64% reduce 0%
17/03/10 10:16:16 INFO mapreduce.Job:  map 67% reduce 0%
17/03/10 10:16:19 INFO mapreduce.Job:  map 71% reduce 0%
17/03/10 10:16:22 INFO mapreduce.Job:  map 74% reduce 0%
17/03/10 10:16:25 INFO mapreduce.Job:  map 76% reduce 0%
17/03/10 10:16:28 INFO mapreduce.Job:  map 79% reduce 0%
17/03/10 10:16:31 INFO mapreduce.Job:  map 83% reduce 0%
17/03/10 10:16:34 INFO mapreduce.Job:  map 86% reduce 0%
17/03/10 10:16:37 INFO mapreduce.Job:  map 88% reduce 0%
17/03/10 10:16:40 INFO mapreduce.Job:  map 92% reduce 0%
17/03/10 10:16:52 INFO mapreduce.Job:  map 100% reduce 0%
17/03/10 10:16:53 INFO mapreduce.Job: Job job_1489140033717_0002 completed successfully
17/03/10 10:16:53 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=985408
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=682
		HDFS: Number of bytes written=6553600000
		HDFS: Number of read operations=32
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters 
		Launched map tasks=8
		Other local map tasks=8
		Total time spent by all maps in occupied slots (ms)=719130
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=719130
		Total vcore-seconds taken by all map tasks=719130
		Total megabyte-seconds taken by all map tasks=736389120
	Map-Reduce Framework
		Map input records=65536000
		Map output records=65536000
		Input split bytes=682
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1625
		CPU time spent (ms)=131370
		Physical memory (bytes) snapshot=3105460224
		Virtual memory (bytes) snapshot=22237024256
		Total committed heap usage (bytes)=2875719680
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=140750829423462787
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=6553600000
```

* Result of time command

```sh
real	1m50.370s
user	0m7.063s
sys	0m0.802s
```

* contentes of path

```sh
[neymar@ip-10-0-1-107 ~]$ hdfs dfs -ls /user/neymar/tgen640
Found 9 items
-rw-r--r--   3 neymar neymar          0 2017-03-10 10:16 /user/neymar/tgen640/_SUCCESS
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00000
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00001
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00002
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00003
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00004
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00005
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00006
-rw-r--r--   3 neymar neymar  819200000 2017-03-10 10:16 /user/neymar/tgen640/part-m-00007
```

* The command and output to show how many blocks are stored under this directory

```sh
[neymar@ip-10-0-1-107 ~]$ hdfs fsck /user/neymar/tgen640
Connecting to namenode via http://ip-10-0-1-107.eu-west-1.compute.internal:50070
FSCK started by neymar (auth:SIMPLE) from /10.0.1.107 for path /user/neymar/tgen640 at Fri Mar 10 10:22:19 UTC 2017
.........Status: HEALTHY
 Total size:	6553600000 B
 Total dirs:	1
 Total files:	9
 Total symlinks:		0
 Total blocks (validated):	56 (avg. block size 117028571 B)
 Minimally replicated blocks:	56 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Fri Mar 10 10:22:19 UTC 2017 in 4 milliseconds


The filesystem under path '/user/neymar/tgen640' is HEALTHY
```

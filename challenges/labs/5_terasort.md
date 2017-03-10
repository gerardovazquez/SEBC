* Teragen Neymar

```sh
[neymar@ip-10-0-1-107 ~]$ kinit neymar
Password for neymar@GERARDOVAZQUEZ.ES: 
[neymar@ip-10-0-1-107 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort -Dmapreduce.job.maps=8 -Dmapreduce.job.reduces=8 tgen640 tsort640m 1>terasort.out 2>terasort.err
```

```sh
17/03/10 11:10:42 INFO terasort.TeraSort: starting
17/03/10 11:10:45 INFO hdfs.DFSClient: Created token for neymar: HDFS_DELEGATION_TOKEN owner=neymar@GERARDOVAZQUEZ.ES, renewer=yarn, realUser=, issueDate=1489144245153, maxDate=1489749045153, sequenceNumber=6, masterKeyId=4 on 10.0.1.107:8020
17/03/10 11:10:45 INFO security.TokenCache: Got dt for hdfs://ip-10-0-1-107.eu-west-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.1.107:8020, Ident: (token for neymar: HDFS_DELEGATION_TOKEN owner=neymar@GERARDOVAZQUEZ.ES, renewer=yarn, realUser=, issueDate=1489144245153, maxDate=1489749045153, sequenceNumber=6, masterKeyId=4)
17/03/10 11:10:45 INFO input.FileInputFormat: Total input paths to process : 8
17/03/10 11:10:46 INFO client.RMProxy: Connecting to ResourceManager at ip-10-0-1-107.eu-west-1.compute.internal/10.0.1.107:8032
17/03/10 11:10:46 INFO mapreduce.JobSubmitter: number of splits:56
17/03/10 11:10:47 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1489144195229_0001
17/03/10 11:10:47 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.1.107:8020, Ident: (token for neymar: HDFS_DELEGATION_TOKEN owner=neymar@GERARDOVAZQUEZ.ES, renewer=yarn, realUser=, issueDate=1489144245153, maxDate=1489749045153, sequenceNumber=6, masterKeyId=4)
17/03/10 11:10:48 INFO impl.YarnClientImpl: Submitted application application_1489144195229_0001
17/03/10 11:10:48 INFO mapreduce.Job: The url to track the job: http://ip-10-0-1-107.eu-west-1.compute.internal:8088/proxy/application_1489144195229_0001/
17/03/10 11:10:48 INFO mapreduce.Job: Running job: job_1489144195229_0001
17/03/10 11:10:58 INFO mapreduce.Job: Job job_1489144195229_0001 running in uber mode : false
17/03/10 11:10:58 INFO mapreduce.Job:  map 0% reduce 0%
17/03/10 11:11:10 INFO mapreduce.Job:  map 4% reduce 0%
17/03/10 11:11:17 INFO mapreduce.Job:  map 6% reduce 0%
17/03/10 11:11:18 INFO mapreduce.Job:  map 11% reduce 0%
17/03/10 11:11:19 INFO mapreduce.Job:  map 13% reduce 0%
17/03/10 11:11:20 INFO mapreduce.Job:  map 14% reduce 0%
17/03/10 11:11:22 INFO mapreduce.Job:  map 18% reduce 0%
17/03/10 11:11:29 INFO mapreduce.Job:  map 19% reduce 0%
17/03/10 11:11:31 INFO mapreduce.Job:  map 26% reduce 0%
17/03/10 11:11:33 INFO mapreduce.Job:  map 32% reduce 0%
17/03/10 11:11:42 INFO mapreduce.Job:  map 33% reduce 0%
17/03/10 11:11:43 INFO mapreduce.Job:  map 36% reduce 0%
17/03/10 11:11:44 INFO mapreduce.Job:  map 38% reduce 0%
17/03/10 11:11:45 INFO mapreduce.Job:  map 44% reduce 0%
17/03/10 11:11:46 INFO mapreduce.Job:  map 46% reduce 0%
17/03/10 11:11:53 INFO mapreduce.Job:  map 48% reduce 0%
17/03/10 11:11:54 INFO mapreduce.Job:  map 50% reduce 0%
17/03/10 11:11:55 INFO mapreduce.Job:  map 51% reduce 0%
17/03/10 11:11:56 INFO mapreduce.Job:  map 52% reduce 0%
17/03/10 11:11:57 INFO mapreduce.Job:  map 53% reduce 0%
17/03/10 11:11:58 INFO mapreduce.Job:  map 57% reduce 0%
17/03/10 11:11:59 INFO mapreduce.Job:  map 60% reduce 0%
17/03/10 11:12:00 INFO mapreduce.Job:  map 61% reduce 0%
17/03/10 11:12:04 INFO mapreduce.Job:  map 64% reduce 0%
17/03/10 11:12:08 INFO mapreduce.Job:  map 65% reduce 0%
17/03/10 11:12:09 INFO mapreduce.Job:  map 67% reduce 0%
17/03/10 11:12:11 INFO mapreduce.Job:  map 70% reduce 0%
17/03/10 11:12:12 INFO mapreduce.Job:  map 73% reduce 0%
17/03/10 11:12:13 INFO mapreduce.Job:  map 75% reduce 0%
17/03/10 11:12:14 INFO mapreduce.Job:  map 76% reduce 0%
17/03/10 11:12:15 INFO mapreduce.Job:  map 78% reduce 0%
17/03/10 11:12:16 INFO mapreduce.Job:  map 79% reduce 0%
17/03/10 11:12:21 INFO mapreduce.Job:  map 82% reduce 0%
17/03/10 11:12:22 INFO mapreduce.Job:  map 86% reduce 0%
17/03/10 11:12:23 INFO mapreduce.Job:  map 87% reduce 0%
17/03/10 11:12:24 INFO mapreduce.Job:  map 90% reduce 0%
17/03/10 11:12:25 INFO mapreduce.Job:  map 91% reduce 0%
17/03/10 11:12:29 INFO mapreduce.Job:  map 95% reduce 0%
17/03/10 11:12:30 INFO mapreduce.Job:  map 96% reduce 0%
17/03/10 11:12:35 INFO mapreduce.Job:  map 100% reduce 0%
17/03/10 11:12:36 INFO mapreduce.Job:  map 100% reduce 2%
17/03/10 11:12:37 INFO mapreduce.Job:  map 100% reduce 5%
17/03/10 11:12:39 INFO mapreduce.Job:  map 100% reduce 9%
17/03/10 11:12:40 INFO mapreduce.Job:  map 100% reduce 11%
17/03/10 11:12:42 INFO mapreduce.Job:  map 100% reduce 14%
17/03/10 11:12:43 INFO mapreduce.Job:  map 100% reduce 16%
17/03/10 11:12:45 INFO mapreduce.Job:  map 100% reduce 23%
17/03/10 11:12:47 INFO mapreduce.Job:  map 100% reduce 26%
17/03/10 11:12:49 INFO mapreduce.Job:  map 100% reduce 27%
17/03/10 11:12:51 INFO mapreduce.Job:  map 100% reduce 28%
17/03/10 11:12:53 INFO mapreduce.Job:  map 100% reduce 29%
17/03/10 11:12:56 INFO mapreduce.Job:  map 100% reduce 32%
17/03/10 11:12:57 INFO mapreduce.Job:  map 100% reduce 33%
17/03/10 11:12:59 INFO mapreduce.Job:  map 100% reduce 36%
17/03/10 11:13:00 INFO mapreduce.Job:  map 100% reduce 37%
17/03/10 11:13:01 INFO mapreduce.Job:  map 100% reduce 41%
17/03/10 11:13:02 INFO mapreduce.Job:  map 100% reduce 44%
17/03/10 11:13:03 INFO mapreduce.Job:  map 100% reduce 45%
17/03/10 11:13:04 INFO mapreduce.Job:  map 100% reduce 49%
17/03/10 11:13:05 INFO mapreduce.Job:  map 100% reduce 55%
17/03/10 11:13:06 INFO mapreduce.Job:  map 100% reduce 57%
17/03/10 11:13:07 INFO mapreduce.Job:  map 100% reduce 59%
17/03/10 11:13:08 INFO mapreduce.Job:  map 100% reduce 64%
17/03/10 11:13:09 INFO mapreduce.Job:  map 100% reduce 66%
17/03/10 11:13:11 INFO mapreduce.Job:  map 100% reduce 68%
17/03/10 11:13:13 INFO mapreduce.Job:  map 100% reduce 69%
17/03/10 11:13:14 INFO mapreduce.Job:  map 100% reduce 74%
17/03/10 11:13:15 INFO mapreduce.Job:  map 100% reduce 76%
17/03/10 11:13:16 INFO mapreduce.Job:  map 100% reduce 77%
17/03/10 11:13:17 INFO mapreduce.Job:  map 100% reduce 82%
17/03/10 11:13:18 INFO mapreduce.Job:  map 100% reduce 85%
17/03/10 11:13:19 INFO mapreduce.Job:  map 100% reduce 86%
17/03/10 11:13:20 INFO mapreduce.Job:  map 100% reduce 88%
17/03/10 11:13:21 INFO mapreduce.Job:  map 100% reduce 90%
17/03/10 11:13:23 INFO mapreduce.Job:  map 100% reduce 91%
17/03/10 11:13:24 INFO mapreduce.Job:  map 100% reduce 92%
17/03/10 11:13:26 INFO mapreduce.Job:  map 100% reduce 93%
17/03/10 11:13:27 INFO mapreduce.Job:  map 100% reduce 94%
17/03/10 11:13:29 INFO mapreduce.Job:  map 100% reduce 95%
17/03/10 11:13:30 INFO mapreduce.Job:  map 100% reduce 96%
17/03/10 11:13:33 INFO mapreduce.Job:  map 100% reduce 98%
17/03/10 11:13:35 INFO mapreduce.Job:  map 100% reduce 99%
17/03/10 11:13:36 INFO mapreduce.Job:  map 100% reduce 100%
17/03/10 11:13:36 INFO mapreduce.Job: Job job_1489144195229_0001 completed successfully
17/03/10 11:13:36 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=2932744462
		FILE: Number of bytes written=5826341746
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=6553608400
		HDFS: Number of bytes written=6553600000
		HDFS: Number of read operations=192
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters 
		Launched map tasks=56
		Launched reduce tasks=8
		Data-local map tasks=56
		Total time spent by all maps in occupied slots (ms)=640190
		Total time spent by all reduces in occupied slots (ms)=296072
		Total time spent by all map tasks (ms)=640190
		Total time spent by all reduce tasks (ms)=296072
		Total vcore-seconds taken by all map tasks=640190
		Total vcore-seconds taken by all reduce tasks=296072
		Total megabyte-seconds taken by all map tasks=655554560
		Total megabyte-seconds taken by all reduce tasks=303177728
	Map-Reduce Framework
		Map input records=65536000
		Map output records=65536000
		Map output bytes=6684672000
		Map output materialized bytes=2885580998
		Input split bytes=8400
		Combine input records=0
		Combine output records=0
		Reduce input groups=65536000
		Reduce shuffle bytes=2885580998
		Reduce input records=65536000
		Reduce output records=65536000
		Spilled Records=131072000
		Shuffled Maps =448
		Failed Shuffles=0
		Merged Map outputs=448
		GC time elapsed (ms)=14538
		CPU time spent (ms)=663390
		Physical memory (bytes) snapshot=35163779072
		Virtual memory (bytes) snapshot=177578283008
		Total committed heap usage (bytes)=36120297472
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=6553600000
	File Output Format Counters 
		Bytes Written=6553600000
17/03/10 11:13:36 INFO terasort.TeraSort: done
```
```sh
[ronaldo@ip-10-0-1-204 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar pi 10 100
```

```sh
Number of Maps  = 10
Samples per Map = 100
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
17/03/10 11:12:12 INFO client.RMProxy: Connecting to ResourceManager at ip-10-0-1-107.eu-west-1.compute.internal/10.0.1.107:8032
17/03/10 11:12:13 INFO hdfs.DFSClient: Created token for ronaldo: HDFS_DELEGATION_TOKEN owner=ronaldo@GERARDOVAZQUEZ.ES, renewer=yarn, realUser=, issueDate=1489144333320, maxDate=1489749133320, sequenceNumber=7, masterKeyId=4 on 10.0.1.107:8020
17/03/10 11:12:13 INFO security.TokenCache: Got dt for hdfs://ip-10-0-1-107.eu-west-1.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.1.107:8020, Ident: (token for ronaldo: HDFS_DELEGATION_TOKEN owner=ronaldo@GERARDOVAZQUEZ.ES, renewer=yarn, realUser=, issueDate=1489144333320, maxDate=1489749133320, sequenceNumber=7, masterKeyId=4)
17/03/10 11:12:13 INFO input.FileInputFormat: Total input paths to process : 10
17/03/10 11:12:14 INFO mapreduce.JobSubmitter: number of splits:10
17/03/10 11:12:14 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1489144195229_0002
17/03/10 11:12:14 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 10.0.1.107:8020, Ident: (token for ronaldo: HDFS_DELEGATION_TOKEN owner=ronaldo@GERARDOVAZQUEZ.ES, renewer=yarn, realUser=, issueDate=1489144333320, maxDate=1489749133320, sequenceNumber=7, masterKeyId=4)
17/03/10 11:12:14 INFO impl.YarnClientImpl: Submitted application application_1489144195229_0002
17/03/10 11:12:14 INFO mapreduce.Job: The url to track the job: http://ip-10-0-1-107.eu-west-1.compute.internal:8088/proxy/application_1489144195229_0002/
17/03/10 11:12:14 INFO mapreduce.Job: Running job: job_1489144195229_0002
17/03/10 11:12:28 INFO mapreduce.Job: Job job_1489144195229_0002 running in uber mode : false
17/03/10 11:12:28 INFO mapreduce.Job:  map 0% reduce 0%
17/03/10 11:12:39 INFO mapreduce.Job:  map 10% reduce 0%
17/03/10 11:12:42 INFO mapreduce.Job:  map 30% reduce 0%
17/03/10 11:12:43 INFO mapreduce.Job:  map 50% reduce 0%
17/03/10 11:12:46 INFO mapreduce.Job:  map 60% reduce 0%
17/03/10 11:12:50 INFO mapreduce.Job:  map 70% reduce 0%
17/03/10 11:12:51 INFO mapreduce.Job:  map 90% reduce 0%
17/03/10 11:12:54 INFO mapreduce.Job:  map 100% reduce 0%
17/03/10 11:13:17 INFO mapreduce.Job:  map 100% reduce 100%
17/03/10 11:13:17 INFO mapreduce.Job: Job job_1489144195229_0002 completed successfully
17/03/10 11:13:18 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=95
		FILE: Number of bytes written=1369528
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=2980
		HDFS: Number of bytes written=215
		HDFS: Number of read operations=43
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Job Counters 
		Launched map tasks=10
		Launched reduce tasks=1
		Data-local map tasks=10
		Total time spent by all maps in occupied slots (ms)=59637
		Total time spent by all reduces in occupied slots (ms)=5670
		Total time spent by all map tasks (ms)=59637
		Total time spent by all reduce tasks (ms)=5670
		Total vcore-seconds taken by all map tasks=59637
		Total vcore-seconds taken by all reduce tasks=5670
		Total megabyte-seconds taken by all map tasks=61068288
		Total megabyte-seconds taken by all reduce tasks=5806080
	Map-Reduce Framework
		Map input records=10
		Map output records=20
		Map output bytes=180
		Map output materialized bytes=340
		Input split bytes=1800
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=340
		Reduce input records=20
		Reduce output records=0
		Spilled Records=40
		Shuffled Maps =10
		Failed Shuffles=0
		Merged Map outputs=10
		GC time elapsed (ms)=979
		CPU time spent (ms)=9420
		Physical memory (bytes) snapshot=4622884864
		Virtual memory (bytes) snapshot=30486482944
		Total committed heap usage (bytes)=4744806400
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=1180
	File Output Format Counters 
		Bytes Written=97
Job Finished in 65.282 seconds
Estimated value of Pi is 3.14800000000000000000
```

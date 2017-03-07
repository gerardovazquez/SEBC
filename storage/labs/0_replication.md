# Replication

## Open AWS Security Groups for remote cluster

## Set users and paths

```sh
[root@ip-10-0-1-128 ~]# useradd andrzej-jedrzejewski
[root@ip-10-0-1-128 ~]# useradd gerardovazquez
```

```sh
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -mkdir /user/gerardovazquez
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -chown gerardovazquez:gerardovazquez /user/gerardovazquez
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -mkdir /user/andrzej-jedrzejewski
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -chown andrzej-jedrzejewski:andrzej-jedrzejewski /user/andrzej-jedrzejewski
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -mkdir -p /data/gerardovazquez
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -mkdir -p /data/andrzej-jedrzejewski
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -chmod 777 /data/andrzej-jedrzejewski
[root@ip-10-0-1-177 ~]# sudo -u hdfs hdfs dfs -chmod 777 /data/gerardovazquez
```

# Set /etc/hosts

```sh
34.250.173.172  ip-10-0-0-206.eu-west-1.compute.internal
34.250.134.251  ip-10-0-0-106.eu-west-1.compute.internal
34.249.155.8  ip-10-0-0-149.eu-west-1.compute.internal
34.250.246.51  ip-10-0-0-173.eu-west-1.compute.internal
34.251.97.72  ip-10-0-0-93.eu-west-1.compute.internal
```


# Create file with terangen

```sh
[gerardovazquez@ip-10-0-1-177 ~] hadoop jar  /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapred.map.tasks=1 -Dmapred.map.tasks.speculative.execution=false 5242880 /data/gerardovazquez
```

# replicate from remote cluster

```sh
[gerardovazquez@ip-10-0-1-177 ~] hadoop distcp webhdfs://34.250.173.172/data/andrzej-jedrzejewski hdfs://ip-10-0-1-112.eu-west-1.compute.internal/data/andrzej-jedrzejewski
```

Failed if we dont use webhdfs due DNS resolution.

# BRS to remote cluster

Failed due private internal IP binding on clusters

```sh
2017-03-07 11:24:11,858 WARN [main] org.apache.hadoop.hdfs.DFSClient: Failed to connect to /10.0.0.93:50010 for block, add to deadNodes and continue. org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.0.0.93:50010]
org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/10.0.0.93:50010]
	at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:533)
	at org.apache.hadoop.hdfs.DFSClient.newConnectedPeer(DFSClient.java:3527)
	at org.apache.hadoop.hdfs.BlockReaderFactory.nextTcpPeer(BlockReaderFactory.java:840)
	at org.apache.hadoop.hdfs.BlockReaderFactory.getRemoteBlockReaderFromTcp(BlockReaderFactory.java:755)
	at org.apache.hadoop.hdfs.BlockReaderFactory.build(BlockReaderFactory.java:376)
	at org.apache.hadoop.hdfs.DFSInputStream.blockSeekTo(DFSInputStream.java:662)
	at org.apache.hadoop.hdfs.DFSInputStream.readWithStrategy(DFSInputStream.java:889)
	at org.apache.hadoop.hdfs.DFSInputStream.read(DFSInputStream.java:942)
	at java.io.DataInputStream.read(DataInputStream.java:149)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:284)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:345)
	at java.io.FilterInputStream.read(FilterInputStream.java:107)
	at com.cloudera.enterprise.distcp.util.ThrottledInputStream.read(ThrottledInputStream.java:77)
	at com.cloudera.enterprise.distcp.mapred.RetriableFileCopyCommand.readBytes(RetriableFileCopyCommand.java:294)
	at com.cloudera.enterprise.distcp.mapred.RetriableFileCopyCommand.copyToFile(RetriableFileCopyCommand.java:275)
	at com.cloudera.enterprise.distcp.mapred.RetriableFileCopyCommand.doExecute(RetriableFileCopyCommand.java:125)
	at com.cloudera.enterprise.distcp.util.RetriableCommand.execute(RetriableCommand.java:87)
	at com.cloudera.enterprise.distcp.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:510)
	at com.cloudera.enterprise.distcp.mapred.CopyMapper.map(CopyMapper.java:368)
	at com.cloudera.enterprise.distcp.mapred.CopyMapper.map(CopyMapper.java:61)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:422)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1783)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
```

Fixed after setting Datanodes to use Hostnames


# Brownse results

```sh
[gerardovazquez@ip-10-0-1-177 ~]$ hdfs fsck /data/andrzej-jedrzejewski -files -blocks
Connecting to namenode via http://ip-10-0-1-112.eu-west-1.compute.internal:50070
FSCK started by gerardovazquez (auth:SIMPLE) from /10.0.1.177 for path /data/andrzej-jedrzejewski at Tue Mar 07 11:21:03 UTC 2017
/data/andrzej-jedrzejewski <dir>
/data/andrzej-jedrzejewski/_SUCCESS 0 bytes, 0 block(s):  OK

/data/andrzej-jedrzejewski/andrzej-jedrzejewski <dir>
/data/andrzej-jedrzejewski/andrzej-jedrzejewski/_SUCCESS 0 bytes, 0 block(s):  OK

/data/andrzej-jedrzejewski/andrzej-jedrzejewski/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-1372971648-10.0.1.112-1488846802618:blk_1073742903_2079 len=134217728 Live_repl=3
1. BP-1372971648-10.0.1.112-1488846802618:blk_1073742905_2081 len=134217728 Live_repl=3
2. BP-1372971648-10.0.1.112-1488846802618:blk_1073742906_2082 len=134217728 Live_repl=3
3. BP-1372971648-10.0.1.112-1488846802618:blk_1073742907_2083 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	2
 Total files:	3
 Total symlinks:		0 (Files currently being written: 1)
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue Mar 07 11:21:03 UTC 2017 in 3 milliseconds


The filesystem under path '/data/andrzej-jedrzejewski' is HEALTHY
```

```sh
[gerardovazquez@ip-10-0-1-177 ~]$ hdfs fsck /data/gerardovazquez -files -blocks
Connecting to namenode via http://ip-10-0-1-112.eu-west-1.compute.internal:50070
FSCK started by gerardovazquez (auth:SIMPLE) from /10.0.1.177 for path /data/gerardovazquez at Tue Mar 07 11:22:10 UTC 2017
/data/gerardovazquez <dir>
/data/gerardovazquez/_SUCCESS 0 bytes, 0 block(s):  OK

/data/gerardovazquez/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-1372971648-10.0.1.112-1488846802618:blk_1073742728_1904 len=134217728 Live_repl=3
1. BP-1372971648-10.0.1.112-1488846802618:blk_1073742729_1905 len=134217728 Live_repl=3
2. BP-1372971648-10.0.1.112-1488846802618:blk_1073742730_1906 len=134217728 Live_repl=3
3. BP-1372971648-10.0.1.112-1488846802618:blk_1073742731_1907 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	1
 Total files:	2
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue Mar 07 11:22:10 UTC 2017 in 1 milliseconds


The filesystem under path '/data/gerardovazquez' is HEALTHY
```

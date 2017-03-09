# YARN Test script

* Added more mem, map, reduce test and generate CSV file

```sh
#!/bin/sh
# Confirm the path values given below correspond to your installation

MR=/opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce
HADOOP=/opt/cloudera/parcels/CDH/bin

# CSV file
RECORD_FILE=/home/gerardovazquez/perf-test.csv

# Mark start of the loop
echo Testing loop started on `date`

# Mapper containers
for i in 1  3  5  7 9    
do
   # Reducer containers
   for j in 1  3  5  7 9 
   do                 
      # Container memory
      for k in 512 768 1024
      do                         
         # Set mapper JVM heap 
         MAP_MB=`echo "($k*0.8)/1" | bc` 

         # Set reducer JVM heap 
         RED_MB=`echo "($k*0.8)/1" | bc` 
    
        echo "Num_MAP: ${i}; Num_RED: ${j} - MAP: ${MAP_MB} ; RED: ${RED_MB}"

        echo "Runining Teragen"
        start=$(date +%s)
        time ${HADOOP}/hadoop jar ${MR}/hadoop-examples.jar teragen \
                     -Dmapreduce.job.maps=$i \
                     -Dmapreduce.map.memory.mb=$k \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                      51200000 /results/tg-10GB-${i}-${j}-${k} 1>tera_${i}_${j}_${k}.out 2>tera_${i}_${j}_${k}.err
        teragent=$(echo "$(date +%s.%N) - $start" | bc) 

        start=$(date +%s)
        echo "Running Terasort" 
        time ${HADOOP}/hadoop jar ${MR}/hadoop-examples.jar terasort \
                     -Dmapreduce.job.maps=$i \
                     -Dmapreduce.job.reduces=$j \
                     -Dmapreduce.map.memory.mb=$k \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                     -Dmapreduce.reduce.memory.mb=$k \
                     -Dmapreduce.reduce.java.opts.max.heap=$RED_MB \
	             /results/tg-10GB-${i}-${j}-${k}  \
                     /results/ts-10GB-${i}-${j}-${k} 1>>tera_${i}_${j}_${k}.out 2>>tera_${i}_${j}_${k}.err
        terasortt=$(echo "$(date +%s) - $start" | bc)

        echo "Removing folders"
        $HADOOP/hadoop fs -rm -r -skipTrash /results/tg-10GB-${i}-${j}-${k}                         
        $HADOOP/hadoop fs -rm -r -skipTrash /results/ts-10GB-${i}-${j}-${k}                 
        echo "${i},${j},${k},${teragent%.*},${terasortt%.*}" >> ${RECORD_FILE}
      done
   done
done

echo Testing loop ended on `date`
```

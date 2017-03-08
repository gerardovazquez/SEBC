# Use The API

* Stop hive

```sh
curl -X POST -u 'gerardovazquez:cloudera' 'http://cloudera01:7180/api/v1/clusters/gerardovazquez/services/hive/commands/stop'
{
  "id" : 543,
  "name" : "Stop",
  "startTime" : "2017-03-08T10:47:56.675Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

* Start hive

```sh
gerardovazquez@INV00710:~$ curl -X POST -u 'gerardovazquez:cloudera' 'http://cloudera01:7180/api/v1/clusters/gerardovazquez/services/hie/commands/start'
{
  "id" : 547,
  "name" : "Start",
  "startTime" : "2017-03-08T10:48:43.994Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

* Check hive status

```sh
gerardovazquez@INV00710:~$ curl -X GET -u 'gerardovazquez:cloudera' 'http://cloudera01:7180/api/v1/clusters/gerardovazquez/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-10-0-1-128.eu-west-1.compute.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false
}
```
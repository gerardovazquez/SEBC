HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=ginlmgwappxj7kmvyckzoc1l;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 08 Mar 2017 10:45:15 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "timestamp" : "2017-03-08T10:45:15.636Z",
  "clusters" : [ {
    "name" : "gerardovazquez",
    "version" : "CDH5",
    "services" : [ {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-53366e9af9545a772745b0e88417429b",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-069c8ba9ba483fa42"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3404ynzue41dhjykhbie1zu24"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-838ecf17d07ba57cf7893dbf6f5185c8",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-065038eb4088b74cf"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dzuubjv5esymp76evpwrtj5eo"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-9a43055b112655c5b511872892f319c5",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-03329b654b3f61b98"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e2chxqy1n3fkmapw61zn2o74e"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-10-0-1-128.eu-west-1.compute.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "*H4rdPassword#"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-452eae34bcba1d443ead04e5acf276ef",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "i-0f934bd7709834eb0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ee63cujnmm33lsb40420xu68k"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-10-0-1-128.eu-west-1.compute.internal"
        }, {
          "name" : "database_password",
          "value" : "*H4rdPassword#"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-94f780409873d2e8e028033ab8571853"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-452eae34bcba1d443ead04e5acf276ef",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "i-0f934bd7709834eb0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7qcmub9efiecmdb5ht7hdbo7o"
          }, {
            "name" : "secret_key",
            "value" : "k31k6Ng5WXxMKeU8zc9paBos2jgPN6"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "717225984"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn,/data/01/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "10555519795"
          }, {
            "name" : "dfs_datanode_failed_volumes_tolerated",
            "value" : "1"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "200"
          }, {
            "name" : "rm_io_weight",
            "value" : "100"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/data/01/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn,/data/01/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "717225984"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/data/01/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "717225984"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_client_use_datanode_hostname",
          "value" : "true"
        }, {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "iGe1dktlRQtA7x8iKyEMtXXXMNRRGr"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "bVfPtGgLQWCNV8X6REvVQNCGgnGjze"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "E4VXNExd6u5wiBe98RmHdGY5dxPY9e"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-94f780409873d2e8e028033ab8571853",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-53366e9af9545a772745b0e88417429b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-069c8ba9ba483fa42"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8rlx78l7zp249zx7fjd01tjfd"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-838ecf17d07ba57cf7893dbf6f5185c8",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-065038eb4088b74cf"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "e56ev0uahwdywyoymj5j5cad5"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-9a43055b112655c5b511872892f319c5",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-03329b654b3f61b98"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "26kr16xr3f34mp3zioiumcqzl"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-452eae34bcba1d443ead04e5acf276ef",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-0f934bd7709834eb0"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cdoublw3rcl8qzuxr6kb53ky3"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-94f780409873d2e8e028033ab8571853",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7t7xaqeeza2cgpqlm8erub4ds"
          } ]
        }
      }, {
        "name" : "hdfs-GATEWAY-452eae34bcba1d443ead04e5acf276ef",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0f934bd7709834eb0"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-53366e9af9545a772745b0e88417429b",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-069c8ba9ba483fa42"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "wd8e4iqraw9gq7ycu2m6u5am"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-838ecf17d07ba57cf7893dbf6f5185c8",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-065038eb4088b74cf"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8dhxm7m4h0dgjxnw77lrndqds"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-9a43055b112655c5b511872892f319c5",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-03329b654b3f61b98"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8h3sbb7w6g6uilzi2u85zoel4"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-452eae34bcba1d443ead04e5acf276ef",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-0f934bd7709834eb0"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "57"
          }, {
            "name" : "role_jceks_password",
            "value" : "dmkylij1526x1rw1da19r2245"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-94f780409873d2e8e028033ab8571853",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1"
          }, {
            "name" : "namenode_id",
            "value" : "43"
          }, {
            "name" : "role_jceks_password",
            "value" : "9t7zuv2fkqlx2kzk4rsfof73k"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "6"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "717225984"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1800"
          }, {
            "name" : "rm_io_weight",
            "value" : "900"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm,/data/01/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs,/data/01/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "3150"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "717225984"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "3150"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "7Abc47jfRwkZtms0gPzy0t1LNwgxd0"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-GATEWAY-452eae34bcba1d443ead04e5acf276ef",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0f934bd7709834eb0"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "yarn-JOBHISTORY-94f780409873d2e8e028033ab8571853",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "go31fb5sw9srfckxy3l91kr2"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-53366e9af9545a772745b0e88417429b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-069c8ba9ba483fa42"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "aad1u7sfgnp94o7y7k9sz6skf"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-838ecf17d07ba57cf7893dbf6f5185c8",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-065038eb4088b74cf"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "773h7cza62nphpwkz4nih55k5"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-9a43055b112655c5b511872892f319c5",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-03329b654b3f61b98"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "853r96s3ylrdxetg1669du90e"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-94f780409873d2e8e028033ab8571853",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "49"
          }, {
            "name" : "role_jceks_password",
            "value" : "4mfkwmx9mm4m1deb1j14mjzy0"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "717225984"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "717225984"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "3525050368"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "593"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-10-0-1-128.eu-west-1.compute.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "*H4rdPassword#"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-452eae34bcba1d443ead04e5acf276ef",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0f934bd7709834eb0"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-53366e9af9545a772745b0e88417429b",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-069c8ba9ba483fa42"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-838ecf17d07ba57cf7893dbf6f5185c8",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-065038eb4088b74cf"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-94f780409873d2e8e028033ab8571853",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-9a43055b112655c5b511872892f319c5",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-03329b654b3f61b98"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-94f780409873d2e8e028033ab8571853",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8xrltpaviqog72gyeexyge47y"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-94f780409873d2e8e028033ab8571853",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "i-0d377c493052231e6"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "33eo23vroflr9f1c8t6zgbcwq"
          } ]
        }
      } ],
      "displayName" : "Hive"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "i-0d377c493052231e6",
    "ipAddress" : "10.0.1.112",
    "hostname" : "ip-10-0-1-112.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-0f934bd7709834eb0",
    "ipAddress" : "10.0.1.128",
    "hostname" : "ip-10-0-1-128.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-03329b654b3f61b98",
    "ipAddress" : "10.0.1.177",
    "hostname" : "ip-10-0-1-177.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-069c8ba9ba483fa42",
    "ipAddress" : "10.0.1.180",
    "hostname" : "ip-10-0-1-180.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-065038eb4088b74cf",
    "ipAddress" : "10.0.1.187",
    "hostname" : "ip-10-0-1-187.eu-west-1.compute.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__28ddda34-3bbd-4baf-8b68-a48f354e9f2f",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "0adeea34e9be31a65c8ed66847bc0b446e21d786ed818ccda56219444963ed19",
    "pwSalt" : -4479499861604873815,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-94f780409873d2e8e028033ab8571853",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "3f37cdfae8a9a21840941ef3c03df8320a1dd34b5c3b459444971452453ab97b",
    "pwSalt" : 3284624404195984178,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-94f780409873d2e8e028033ab8571853",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "a5d06d8e8d88783b1ac953c8d60bca2f944db8f50e55bab135b83d2c1b62f001",
    "pwSalt" : 5043202979455787811,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-94f780409873d2e8e028033ab8571853",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "ae19eb13f2bb5c734709b21761881e8a0552a8398e129cb2a3942c16b1295c3f",
    "pwSalt" : 45399467311161365,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-94f780409873d2e8e028033ab8571853",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "68690387a4c3d4d7583ddfecd4837744bd5f0eb7f40e766544a0fce29e8de05a",
    "pwSalt" : 7241040791967500997,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "4bec4e505a62dff29ebf27fee489201d9f21a01d7d458be35813efcffaa89d8f",
    "pwSalt" : 8543568488935034052,
    "pwLogin" : true
  }, {
    "name" : "gerardovazquez",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "8254a3183e1714ca9f18b41dcddfb901490dd9d7397c0030e2e9dcb10267acb5",
    "pwSalt" : -2847025139901081533,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "8b6fb3bd258d415d8fb71e1f330dd9641680f7ad26120b571c2d25273dfe97e8",
    "pwSalt" : -1292309789285370977,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.8.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20161019-1014",
    "gitHash" : "518f0d6d44abc87bc392646e4369a20c8192b7cf",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "717225984"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "717225984"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "933232640"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-10-0-1-128.eu-west-1.compute.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "*H4rdPassword#"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "717225984"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "717225984"
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "933232640"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-94f780409873d2e8e028033ab8571853",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "i-0d377c493052231e6"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "b4ws2k7z6hikd788y3p7m2b9g"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-94f780409873d2e8e028033ab8571853",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "i-0d377c493052231e6"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "23hbobpffcewf3eecfg5zthu"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-94f780409873d2e8e028033ab8571853",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "i-0d377c493052231e6"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "cgjoh1xj5zqto4e6mwbo40zj7"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-94f780409873d2e8e028033ab8571853",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "i-0d377c493052231e6"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "coiu2grt5tk0blc1683r25t2r"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-94f780409873d2e8e028033ab8571853",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "i-0d377c493052231e6"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "ch9aqmna3otmidar2kt2ftwfj"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/24/2012 19:30"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/,http://ip-10-0-1-128.eu-west-1.compute.internal/cdh5.10.0,http://ip-10-0-1-128.eu-west-1.compute.internal/cdh5.8.4"
    } ]
  }
}
```
{
    "timestamp": "2018-10-17T08:41:22.344Z",
    "clusters": [
        {
            "name": "xpruimorais",
            "version": "CDH5",
            "services": [
                {
                    "name": "zookeeper",
                    "type": "ZOOKEEPER",
                    "config": {
                        "roleTypeConfigs": [],
                        "items": []
                    },
                    "roles": [
                        {
                            "name": "zookeeper-SERVER-0af268a0634e96910c9a169abe1f32dd",
                            "type": "SERVER",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "aq3w50fk26t8d6nq2wwx4tj7p"
                                    },
                                    {
                                        "name": "serverId",
                                        "value": "2"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "zookeeper-SERVER-69ff776e4511db9a886df4209553032f",
                            "type": "SERVER",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "4kcpzgly2520vgzxlj6l9ir0z"
                                    },
                                    {
                                        "name": "serverId",
                                        "value": "3"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "zookeeper-SERVER-ab00d625b1b9ae2625c5267d93406a96",
                            "type": "SERVER",
                            "hostRef": {
                                "hostId": "49947731-92f1-42d7-9e38-900447bc12bb"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "8ua9h702mls1reilqld8zqert"
                                    },
                                    {
                                        "name": "serverId",
                                        "value": "1"
                                    }
                                ]
                            }
                        }
                    ],
                    "displayName": "ZooKeeper"
                },
                {
                    "name": "oozie",
                    "type": "OOZIE",
                    "config": {
                        "roleTypeConfigs": [
                            {
                                "roleType": "OOZIE_SERVER",
                                "items": [
                                    {
                                        "name": "oozie_database_host",
                                        "value": "node01.xpandit.com"
                                    },
                                    {
                                        "name": "oozie_database_password",
                                        "value": "oozie_password"
                                    },
                                    {
                                        "name": "oozie_database_type",
                                        "value": "mysql"
                                    },
                                    {
                                        "name": "oozie_database_user",
                                        "value": "oozie"
                                    }
                                ]
                            }
                        ],
                        "items": [
                            {
                                "name": "hive_service",
                                "value": "hive"
                            },
                            {
                                "name": "mapreduce_yarn_service",
                                "value": "yarn"
                            },
                            {
                                "name": "zookeeper_service",
                                "value": "zookeeper"
                            }
                        ]
                    },
                    "roles": [
                        {
                            "name": "oozie-OOZIE_SERVER-69ff776e4511db9a886df4209553032f",
                            "type": "OOZIE_SERVER",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "bm9w66fp8r520eppczhtsvrgy"
                                    }
                                ]
                            }
                        }
                    ],
                    "displayName": "Oozie"
                },
                {
                    "name": "hue",
                    "type": "HUE",
                    "config": {
                        "roleTypeConfigs": [],
                        "items": [
                            {
                                "name": "database_host",
                                "value": "node01.xpandit.com"
                            },
                            {
                                "name": "database_password",
                                "value": "hue_password"
                            },
                            {
                                "name": "database_type",
                                "value": "mysql"
                            },
                            {
                                "name": "hive_service",
                                "value": "hive"
                            },
                            {
                                "name": "hue_webhdfs",
                                "value": "hdfs-HTTPFS-0af268a0634e96910c9a169abe1f32dd"
                            },
                            {
                                "name": "oozie_service",
                                "value": "oozie"
                            },
                            {
                                "name": "zookeeper_service",
                                "value": "zookeeper"
                            }
                        ]
                    },
                    "roles": [
                        {
                            "name": "hue-HUE_LOAD_BALANCER-69ff776e4511db9a886df4209553032f",
                            "type": "HUE_LOAD_BALANCER",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "40ffurl2u5xkn3yvgxkn05ox9"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hue-HUE_SERVER-69ff776e4511db9a886df4209553032f",
                            "type": "HUE_SERVER",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "navmetadataserver_cmdb_password",
                                        "value": "e9294b5f-d9d2-4e6a-8e6e-a66b075adfd9"
                                    },
                                    {
                                        "name": "role_jceks_password",
                                        "value": "zm6lz9kita848sv5bminljjd"
                                    },
                                    {
                                        "name": "secret_key",
                                        "value": "fG3Z5h2PfpqRUVlskBONuTdDx4WWEj"
                                    }
                                ]
                            }
                        }
                    ],
                    "displayName": "Hue"
                },
                {
                    "name": "hdfs",
                    "type": "HDFS",
                    "config": {
                        "roleTypeConfigs": [
                            {
                                "roleType": "DATANODE",
                                "items": [
                                    {
                                        "name": "datanode_java_heapsize",
                                        "value": "1073741824"
                                    },
                                    {
                                        "name": "dfs_data_dir_list",
                                        "value": "/data/01/dfs/dn"
                                    },
                                    {
                                        "name": "dfs_datanode_du_reserved",
                                        "value": "10732070912"
                                    },
                                    {
                                        "name": "dfs_datanode_max_locked_memory",
                                        "value": "4294967296"
                                    },
                                    {
                                        "name": "rm_cpu_shares",
                                        "value": "200"
                                    },
                                    {
                                        "name": "rm_io_weight",
                                        "value": "100"
                                    }
                                ]
                            },
                            {
                                "roleType": "GATEWAY",
                                "items": [
                                    {
                                        "name": "dfs_client_use_trash",
                                        "value": "true"
                                    }
                                ]
                            },
                            {
                                "roleType": "JOURNALNODE",
                                "items": [
                                    {
                                        "name": "dfs_journalnode_edits_dir",
                                        "value": "/data/01/dfs/jn"
                                    }
                                ]
                            },
                            {
                                "roleType": "NAMENODE",
                                "items": [
                                    {
                                        "name": "dfs_name_dir_list",
                                        "value": "/data/01/dfs/nn"
                                    },
                                    {
                                        "name": "dfs_namenode_servicerpc_address",
                                        "value": "8022"
                                    },
                                    {
                                        "name": "namenode_java_heapsize",
                                        "value": "1816133632"
                                    }
                                ]
                            },
                            {
                                "roleType": "SECONDARYNAMENODE",
                                "items": [
                                    {
                                        "name": "fs_checkpoint_dir_list",
                                        "value": "/data/01/dfs/snn"
                                    },
                                    {
                                        "name": "secondary_namenode_java_heapsize",
                                        "value": "1816133632"
                                    }
                                ]
                            }
                        ],
                        "items": [
                            {
                                "name": "dfs_ha_fencing_cloudera_manager_secret_key",
                                "value": "1fqpU1LooHNlixWIxMhAgBwELbD6Tc"
                            },
                            {
                                "name": "fc_authorization_secret_key",
                                "value": "m8xlhFGdx1Pa3nPTR7XeLlRhA2vymI"
                            },
                            {
                                "name": "http_auth_signature_secret",
                                "value": "seMyeN81Ajo4cbEqds15KJoMF7kygJ"
                            },
                            {
                                "name": "rm_dirty",
                                "value": "false"
                            },
                            {
                                "name": "rm_last_allocation_percentage",
                                "value": "10"
                            },
                            {
                                "name": "zookeeper_service",
                                "value": "zookeeper"
                            }
                        ]
                    },
                    "roles": [
                        {
                            "name": "hdfs-BALANCER-0af268a0634e96910c9a169abe1f32dd",
                            "type": "BALANCER",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": []
                            }
                        },
                        {
                            "name": "hdfs-DATANODE-ab00d625b1b9ae2625c5267d93406a96",
                            "type": "DATANODE",
                            "hostRef": {
                                "hostId": "49947731-92f1-42d7-9e38-900447bc12bb"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "2ypb2j2s0eqlc5ueop9ylblk3"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-DATANODE-cb159d43483f045ff6c477e968d87729",
                            "type": "DATANODE",
                            "hostRef": {
                                "hostId": "c497ff77-2597-4768-a5f4-4beb330ab022"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "6g6u049p61ev0s94sagtnwzge"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-DATANODE-ed1d9c967e7aa2205a30a4c2a8db48bf",
                            "type": "DATANODE",
                            "hostRef": {
                                "hostId": "934248a8-9395-4c04-b3fa-0dbbd4d602b4"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "ee9tpzfhmv91qf9o0hod9ziz8"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-FAILOVERCONTROLLER-0af268a0634e96910c9a169abe1f32dd",
                            "type": "FAILOVERCONTROLLER",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "euuh1tpaga88irtg250df270z"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-FAILOVERCONTROLLER-69ff776e4511db9a886df4209553032f",
                            "type": "FAILOVERCONTROLLER",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "58ig22jytbiwxbe38vel6f1go"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-HTTPFS-0af268a0634e96910c9a169abe1f32dd",
                            "type": "HTTPFS",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "42aul8xar8pxuk0js3xs6v6gt"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-JOURNALNODE-0af268a0634e96910c9a169abe1f32dd",
                            "type": "JOURNALNODE",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "f9mar4ueszhhfffueybugari"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-JOURNALNODE-69ff776e4511db9a886df4209553032f",
                            "type": "JOURNALNODE",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "2jk0fzf5oeilgmt6ov0hi9c23"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-JOURNALNODE-ab00d625b1b9ae2625c5267d93406a96",
                            "type": "JOURNALNODE",
                            "hostRef": {
                                "hostId": "49947731-92f1-42d7-9e38-900447bc12bb"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "dkdj8xet04q5hcvrlekhl0fjy"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-NAMENODE-0af268a0634e96910c9a169abe1f32dd",
                            "type": "NAMENODE",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "autofailover_enabled",
                                        "value": "true"
                                    },
                                    {
                                        "name": "dfs_federation_namenode_nameservice",
                                        "value": "xpruimorais"
                                    },
                                    {
                                        "name": "dfs_namenode_quorum_journal_name",
                                        "value": "xpruimorais"
                                    },
                                    {
                                        "name": "namenode_id",
                                        "value": "133"
                                    },
                                    {
                                        "name": "role_jceks_password",
                                        "value": "4kyw99w5ea7klrywshmnaqnoa"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hdfs-NAMENODE-69ff776e4511db9a886df4209553032f",
                            "type": "NAMENODE",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "autofailover_enabled",
                                        "value": "true"
                                    },
                                    {
                                        "name": "dfs_federation_namenode_nameservice",
                                        "value": "xpruimorais"
                                    },
                                    {
                                        "name": "dfs_namenode_quorum_journal_name",
                                        "value": "xpruimorais"
                                    },
                                    {
                                        "name": "namenode_id",
                                        "value": "118"
                                    },
                                    {
                                        "name": "role_jceks_password",
                                        "value": "9xlb0jbizc3zxae6nkb2lgkua"
                                    }
                                ]
                            }
                        }
                    ],
                    "displayName": "HDFS"
                },
                {
                    "name": "yarn",
                    "type": "YARN",
                    "config": {
                        "roleTypeConfigs": [
                            {
                                "roleType": "GATEWAY",
                                "items": [
                                    {
                                        "name": "mapred_reduce_tasks",
                                        "value": "6"
                                    },
                                    {
                                        "name": "mapred_submit_replication",
                                        "value": "3"
                                    }
                                ]
                            },
                            {
                                "roleType": "NODEMANAGER",
                                "items": [
                                    {
                                        "name": "rm_cpu_shares",
                                        "value": "1800"
                                    },
                                    {
                                        "name": "rm_io_weight",
                                        "value": "900"
                                    },
                                    {
                                        "name": "yarn_nodemanager_heartbeat_interval_ms",
                                        "value": "100"
                                    },
                                    {
                                        "name": "yarn_nodemanager_local_dirs",
                                        "value": "/data/01/yarn/nm"
                                    },
                                    {
                                        "name": "yarn_nodemanager_log_dirs",
                                        "value": "/data/01/yarn/container-logs,/mnt/resource/yarn/container-logs"
                                    },
                                    {
                                        "name": "yarn_nodemanager_resource_cpu_vcores",
                                        "value": "2"
                                    },
                                    {
                                        "name": "yarn_nodemanager_resource_memory_mb",
                                        "value": "10240"
                                    }
                                ]
                            },
                            {
                                "roleType": "RESOURCEMANAGER",
                                "items": [
                                    {
                                        "name": "yarn_scheduler_maximum_allocation_mb",
                                        "value": "2048"
                                    },
                                    {
                                        "name": "yarn_scheduler_maximum_allocation_vcores",
                                        "value": "2"
                                    }
                                ]
                            }
                        ],
                        "items": [
                            {
                                "name": "hdfs_service",
                                "value": "hdfs"
                            },
                            {
                                "name": "rm_dirty",
                                "value": "true"
                            },
                            {
                                "name": "rm_last_allocation_percentage",
                                "value": "90"
                            },
                            {
                                "name": "yarn_service_cgroups",
                                "value": "false"
                            },
                            {
                                "name": "yarn_service_lce_always",
                                "value": "false"
                            },
                            {
                                "name": "zk_authorization_secret_key",
                                "value": "gh7PYGAw1hoifuztzzI9GR8wwAQg0w"
                            },
                            {
                                "name": "zookeeper_service",
                                "value": "zookeeper"
                            }
                        ]
                    },
                    "roles": [
                        {
                            "name": "yarn-JOBHISTORY-0af268a0634e96910c9a169abe1f32dd",
                            "type": "JOBHISTORY",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "80pm4ll4v6sb1foqo9umd6yxv"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "yarn-NODEMANAGER-ab00d625b1b9ae2625c5267d93406a96",
                            "type": "NODEMANAGER",
                            "hostRef": {
                                "hostId": "49947731-92f1-42d7-9e38-900447bc12bb"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "1tybjs5124ruyislqz188vyyc"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "yarn-NODEMANAGER-cb159d43483f045ff6c477e968d87729",
                            "type": "NODEMANAGER",
                            "hostRef": {
                                "hostId": "c497ff77-2597-4768-a5f4-4beb330ab022"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "dnqppln3vi6yl20ij10ov3f3b"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "yarn-NODEMANAGER-ed1d9c967e7aa2205a30a4c2a8db48bf",
                            "type": "NODEMANAGER",
                            "hostRef": {
                                "hostId": "934248a8-9395-4c04-b3fa-0dbbd4d602b4"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "br9jmjva57lxiwq2a4nngq25j"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "yarn-RESOURCEMANAGER-0af268a0634e96910c9a169abe1f32dd",
                            "type": "RESOURCEMANAGER",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "rm_id",
                                        "value": "124"
                                    },
                                    {
                                        "name": "role_jceks_password",
                                        "value": "3mrlnhhzv1nenjmrma7r2b317"
                                    }
                                ]
                            }
                        }
                    ],
                    "displayName": "YARN (MR2 Included)"
                },
                {
                    "name": "hive",
                    "type": "HIVE",
                    "config": {
                        "roleTypeConfigs": [
                            {
                                "roleType": "HIVEMETASTORE",
                                "items": [
                                    {
                                        "name": "hive_metastore_java_heapsize",
                                        "value": "2016411648"
                                    },
                                    {
                                        "name": "hive_metastore_server_max_message_size",
                                        "value": "201641164"
                                    }
                                ]
                            },
                            {
                                "roleType": "HIVESERVER2",
                                "items": [
                                    {
                                        "name": "hiveserver2_java_heapsize",
                                        "value": "2016411648"
                                    },
                                    {
                                        "name": "hiveserver2_spark_driver_memory",
                                        "value": "966367641"
                                    },
                                    {
                                        "name": "hiveserver2_spark_executor_cores",
                                        "value": "4"
                                    },
                                    {
                                        "name": "hiveserver2_spark_executor_memory",
                                        "value": "4221147545"
                                    },
                                    {
                                        "name": "hiveserver2_spark_yarn_driver_memory_overhead",
                                        "value": "102"
                                    },
                                    {
                                        "name": "hiveserver2_spark_yarn_executor_memory_overhead",
                                        "value": "710"
                                    }
                                ]
                            }
                        ],
                        "items": [
                            {
                                "name": "hive_metastore_database_host",
                                "value": "node01.xpandit.com"
                            },
                            {
                                "name": "hive_metastore_database_password",
                                "value": "hive_password"
                            },
                            {
                                "name": "mapreduce_yarn_service",
                                "value": "yarn"
                            },
                            {
                                "name": "zookeeper_service",
                                "value": "zookeeper"
                            }
                        ]
                    },
                    "roles": [
                        {
                            "name": "hive-GATEWAY-0af268a0634e96910c9a169abe1f32dd",
                            "type": "GATEWAY",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": []
                            }
                        },
                        {
                            "name": "hive-GATEWAY-69ff776e4511db9a886df4209553032f",
                            "type": "GATEWAY",
                            "hostRef": {
                                "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                            },
                            "config": {
                                "items": []
                            }
                        },
                        {
                            "name": "hive-GATEWAY-ab00d625b1b9ae2625c5267d93406a96",
                            "type": "GATEWAY",
                            "hostRef": {
                                "hostId": "49947731-92f1-42d7-9e38-900447bc12bb"
                            },
                            "config": {
                                "items": []
                            }
                        },
                        {
                            "name": "hive-GATEWAY-cb159d43483f045ff6c477e968d87729",
                            "type": "GATEWAY",
                            "hostRef": {
                                "hostId": "c497ff77-2597-4768-a5f4-4beb330ab022"
                            },
                            "config": {
                                "items": []
                            }
                        },
                        {
                            "name": "hive-GATEWAY-ed1d9c967e7aa2205a30a4c2a8db48bf",
                            "type": "GATEWAY",
                            "hostRef": {
                                "hostId": "934248a8-9395-4c04-b3fa-0dbbd4d602b4"
                            },
                            "config": {
                                "items": []
                            }
                        },
                        {
                            "name": "hive-HIVEMETASTORE-0af268a0634e96910c9a169abe1f32dd",
                            "type": "HIVEMETASTORE",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "75v2a6jictmxxays0xcwuezr2"
                                    }
                                ]
                            }
                        },
                        {
                            "name": "hive-HIVESERVER2-0af268a0634e96910c9a169abe1f32dd",
                            "type": "HIVESERVER2",
                            "hostRef": {
                                "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df"
                            },
                            "config": {
                                "items": [
                                    {
                                        "name": "role_jceks_password",
                                        "value": "588kfvg0gga25sabb4edz0yed"
                                    }
                                ]
                            }
                        }
                    ],
                    "displayName": "Hive"
                }
            ]
        }
    ],
    "hosts": [
        {
            "hostId": "dd150252-8918-4581-8076-56d6f7251954",
            "ipAddress": "10.1.0.4",
            "hostname": "node01.xpandit.com",
            "rackId": "/default",
            "config": {
                "items": []
            }
        },
        {
            "hostId": "f9f4dc5e-5a2c-4bb7-8223-0daa251012df",
            "ipAddress": "10.1.0.5",
            "hostname": "node02.xpandit.com",
            "rackId": "/default",
            "config": {
                "items": []
            }
        },
        {
            "hostId": "49947731-92f1-42d7-9e38-900447bc12bb",
            "ipAddress": "10.1.0.6",
            "hostname": "node03.xpandit.com",
            "rackId": "/default",
            "config": {
                "items": []
            }
        },
        {
            "hostId": "c497ff77-2597-4768-a5f4-4beb330ab022",
            "ipAddress": "10.1.0.7",
            "hostname": "node04.xpandit.com",
            "rackId": "/default",
            "config": {
                "items": []
            }
        },
        {
            "hostId": "934248a8-9395-4c04-b3fa-0dbbd4d602b4",
            "ipAddress": "10.1.0.8",
            "hostname": "node05.xpandit.com",
            "rackId": "/default",
            "config": {
                "items": []
            }
        }
    ],
    "users": [
        {
            "name": "__cloudera_internal_user__hue-HUE_SERVER-69ff776e4511db9a886df4209553032f",
            "roles": [
                "ROLE_NAVIGATOR_ADMIN"
            ],
            "pwHash": "2510ea1d8a577d3704b8ad42c1dc21a334bae95e89b52befea45323432a1c165",
            "pwSalt": 3756261114853334000,
            "pwLogin": true
        },
        {
            "name": "__cloudera_internal_user__mgmt-EVENTSERVER-69ff776e4511db9a886df4209553032f",
            "roles": [
                "ROLE_USER"
            ],
            "pwHash": "7b99028f48ed4ed757b6170592ec4f390567614394ac88401fa76886360968fe",
            "pwSalt": 1448885683594259000,
            "pwLogin": true
        },
        {
            "name": "__cloudera_internal_user__mgmt-HOSTMONITOR-69ff776e4511db9a886df4209553032f",
            "roles": [
                "ROLE_USER"
            ],
            "pwHash": "0bdbdce204ad382a3dd826eacf46168404aebf5fff3bfa296aa85030921712ff",
            "pwSalt": 276300615597535870,
            "pwLogin": true
        },
        {
            "name": "__cloudera_internal_user__mgmt-REPORTSMANAGER-69ff776e4511db9a886df4209553032f",
            "roles": [
                "ROLE_USER"
            ],
            "pwHash": "84f233433b24a792ed036998620277e546b42f36d8fa0aa291dd390afc84dc2d",
            "pwSalt": 8937935806512634000,
            "pwLogin": true
        },
        {
            "name": "__cloudera_internal_user__mgmt-SERVICEMONITOR-69ff776e4511db9a886df4209553032f",
            "roles": [
                "ROLE_USER"
            ],
            "pwHash": "c2d5c8770a8b3c1a891a99ddd9ba980e515174340ab98eb8d59d8de7691779b4",
            "pwSalt": 7096624247101835000,
            "pwLogin": true
        },
        {
            "name": "admin",
            "roles": [
                "ROLE_LIMITED"
            ],
            "pwHash": "264dfce3f6e9c26988f829e0f6bf9e9c3dc303c44c41a42cb4a4aa54bcfde1ff",
            "pwSalt": -9149590888704759000,
            "pwLogin": true
        },
        {
            "name": "minotaur",
            "roles": [
                "ROLE_CONFIGURATOR"
            ],
            "pwHash": "ef4e31ad138db96b8471a7c93b4424ba0e924f4088151fb78b53cb3d9d604ac1",
            "pwSalt": -6003791341842819000,
            "pwLogin": true
        },
        {
            "name": "xpruimorais",
            "roles": [
                "ROLE_ADMIN"
            ],
            "pwHash": "5b40b31626414af16c33f87d2278df542004b6726735c483f992969a361c7f5e",
            "pwSalt": 1236003107837488600,
            "pwLogin": true
        }
    ],
    "versionInfo": {
        "version": "5.13.3",
        "buildUser": "jenkins",
        "buildTimestamp": "20180328-1830",
        "gitHash": "f90c58536c252d70a23bde6d94514d92a1f111d4",
        "snapshot": false
    },
    "managementService": {
        "name": "mgmt",
        "type": "MGMT",
        "config": {
            "roleTypeConfigs": [
                {
                    "roleType": "REPORTSMANAGER",
                    "items": [
                        {
                            "name": "headlamp_database_host",
                            "value": "node01.xpandit.com"
                        },
                        {
                            "name": "headlamp_database_name",
                            "value": "rman"
                        },
                        {
                            "name": "headlamp_database_password",
                            "value": "rman_password"
                        },
                        {
                            "name": "headlamp_database_user",
                            "value": "rman"
                        }
                    ]
                },
                {
                    "roleType": "SERVICEMONITOR",
                    "items": [
                        {
                            "name": "firehose_non_java_memory_bytes",
                            "value": "3221225472"
                        }
                    ]
                }
            ],
            "items": []
        },
        "roles": [
            {
                "name": "mgmt-ALERTPUBLISHER-69ff776e4511db9a886df4209553032f",
                "type": "ALERTPUBLISHER",
                "hostRef": {
                    "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                },
                "config": {
                    "items": [
                        {
                            "name": "role_jceks_password",
                            "value": "cxnrz6rq1nrut9ikdcp76ehvf"
                        }
                    ]
                }
            },
            {
                "name": "mgmt-EVENTSERVER-69ff776e4511db9a886df4209553032f",
                "type": "EVENTSERVER",
                "hostRef": {
                    "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                },
                "config": {
                    "items": [
                        {
                            "name": "role_jceks_password",
                            "value": "8wq8hls726yeqde937x3jwx4z"
                        }
                    ]
                }
            },
            {
                "name": "mgmt-HOSTMONITOR-69ff776e4511db9a886df4209553032f",
                "type": "HOSTMONITOR",
                "hostRef": {
                    "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                },
                "config": {
                    "items": [
                        {
                            "name": "role_jceks_password",
                            "value": "7geykkad5m8y8scdd34f8w1y8"
                        }
                    ]
                }
            },
            {
                "name": "mgmt-REPORTSMANAGER-69ff776e4511db9a886df4209553032f",
                "type": "REPORTSMANAGER",
                "hostRef": {
                    "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                },
                "config": {
                    "items": [
                        {
                            "name": "role_jceks_password",
                            "value": "7gwc6k3obgifs4w9mn4z22ywq"
                        }
                    ]
                }
            },
            {
                "name": "mgmt-SERVICEMONITOR-69ff776e4511db9a886df4209553032f",
                "type": "SERVICEMONITOR",
                "hostRef": {
                    "hostId": "dd150252-8918-4581-8076-56d6f7251954"
                },
                "config": {
                    "items": [
                        {
                            "name": "role_jceks_password",
                            "value": "eiqrywf3ov1i7aw1r1gk1qx00"
                        }
                    ]
                }
            }
        ],
        "displayName": "Cloudera Management Service"
    },
    "managerSettings": {
        "items": [
            {
                "name": "CLUSTER_STATS_START",
                "value": "10/26/2012 10:30"
            },
            {
                "name": "PUBLIC_CLOUD_STATUS",
                "value": "NOT_ON_PUBLIC_CLOUD"
            },
            {
                "name": "REMOTE_PARCEL_REPO_URLS",
                "value": "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,http://archive.cloudera.com/kudu/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
            }
        ]
    }
}
```

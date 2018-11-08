# Overwriting conflict /model_desc/price_distribute.json, expect old TS 0, but it is 1540380886475

```
# hbase shell
hbase > list
hbase > get "kylin_metadata", "/model_desc/price_distribute.json"
hbase > deleteall "kylin_metadata", "/model_desc/price_distribute.json"
```

# 2. Cannot find hive-site.xml in kylin_hadoop_conf_dir

```
java.lang.RuntimeException: Cannot find hive-site.xml in kylin_hadoop_conf_dir: /usr/hdp/2.6.5.0-292/hadoop/conf. In order to enable spark cubing, you must set kylin.env.hadoop-conf-dir to a dir which contains at least core-site.xml, hdfs-site.xml, hive-site.xml, mapred-site.xml, yarn-site.xml
	at org.apache.kylin.engine.spark.SparkExecutable.doWork(SparkExecutable.java:117)
	at org.apache.kylin.job.execution.AbstractExecutable.execute(AbstractExecutable.java:162)
	at org.apache.kylin.job.execution.DefaultChainedExecutable.doWork(DefaultChainedExecutable.java:67)
	at org.apache.kylin.job.execution.AbstractExecutable.execute(AbstractExecutable.java:162)
	at org.apache.kylin.job.impl.threadpool.DefaultScheduler$JobRunner.run(DefaultScheduler.java:300)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)
```

参考：http://kylin.apache.org/docs20/tutorial/cube_spark.html

处理：

```
# ln -s /etc/hive/conf/hive-site.xml /etc/hadoop/conf/hive-site.xml
```

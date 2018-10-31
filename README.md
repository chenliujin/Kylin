# Installation Guide

## Software requirements
- Hadoop: 2.7+
- Hive: 0.13 - 1.2.1+
- HBase: 1.1+
- Spark 2.1.1+
- JDK: 1.7+
- OS: Linux only, CentOS 6.5+ or Ubuntu 16.0.4+

|  | HBase-1.4.5 |
| --- | --- |
| Hadoop-2.7.6 | S |

## Installation Kylin

## 1. ENV

查看 `/etc/hadoop/conf/hadoop-env.sh` 中 `JAVA_HOME` 的环境变量设置，将其改为系统的环境变量

```
# vim /etc/profile.d/java.env.sh
export JAVA_HOME=/usr/jdk64/jdk1.8.0_112
export PATH=$JAVA_HOME/bin:$PATH

# source /etc/profile.d/java.env.sh
```

## 2. Kylin

```
# cd /opt/
# tar -xzvf apache-kylin-2.3.2-bin-hbase1x.tar.gz
# ln -s /opt/apache-kylin-2.3.2-bin/ /opt/kylin
# chown -R hdfs:hadoop kylin --权限
# vim /etc/profile.d/kylin.sh
export KYLIN_HOME=/opt/kylin
export PATH=$KYLIN_HOME/bin:$PATH
```

## 3. Start Kylin

```
# su hdfs
# $KYLIN_HOME/bin/kylin.sh start
```

## 4. Login
- http://hostname:7070/kylin
- username/password is ADMIN/KYLIN

# Example

## 1. 运行 $KYLIN_HOME/bin/sample.sh 脚本

```
# su hdfs
$ $KYLIN_HOME/bin/sample.sh
$ $KYLIN_HOME/bin/kylin.sh stop --重启kylin server 刷新 metadata
$ $KYLIN_HOME/bin/kylin.sh start
```

## 2. 构建 cube

Model -> Cubes -> kylin_sales_cube, 点击 "Action" - "Build"，选择一个 2014-01-01 以后的日期，这是为了选择全部的10000条测试记录。

## 3. Monitor

监控台查看这个任务的执行进度，直到这个任务100%完成。

任务完成

切换到model控制台会发现cube的状态成为了ready，表示可以执行sql查询了

执行过程中，在hive里会生成临时表，待任务100%完成后，这张表会自动删除

## 4. Insight -> New Query

```
select part_dt, sum(price) as total_selled, count(distinct seller_id) as sellers
from kylin_sales
group by part_dt
order by part_dt
```


# 数据类型
* BOOLEAN

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


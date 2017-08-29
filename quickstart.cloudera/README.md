# Cloudera quickstart

This image is part of an integrated project between CDH QuickStart 5.7.0 and Apache Zeppelin 2.7.2.

https://github.com/sebagonella/docker-cdh-zeppelin

**Get this image**

```
$ docker pull sebagonella/quickstart.cloudera:5.7.0
```

**Build this image**

```
$ cd docker-cdh-zeppelin/quickstart.cloudera
$ docker build -t sebagonella/quickstart.cloudera:5.7.0 .
```

**Run a container**

```
$ docker run -d --name quickstart.cloudera \
    -p 7180:7180 \
    -p 8080:8080 \
    -p 8888:8888 \
    -p 2222:22 \
    -p 80:80 \
    -p 4040:4040 \
    -p 8020:8020 \
    -p 8022:8022 \
    -p 8030:8030 \
    -p 8032:8032 \
    -p 8033:8033 \
    -p 8040:8040 \
    -p 8042:8042 \
    -p 8088:8088 \
    -p 8485:8485 \
    -p 9083:9083 \
    -p 10020:10020 \
    -p 10033:10033 \
    -p 18088:18088 \
    -p 19888:19888 \
    -p 25000:25000 \
    -p 25010:25010 \
    -p 25020:25020 \
    -p 50010:50010 \
    -p 50020:50020 \
    -p 50070:50070 \
    --privileged=true -ti sebagonella/quickstart.cloudera:5.7.0 /usr/bin/docker-quickstart 
```

**Links**

ResourceManager - http://localhost:8088

Hue - http://localhost:8888  
user: cloudera  
pass: cloudera 
  
Size docker image after build: 6.46GB

**Example - Get data from DB2 to HDFS using Sqoop**

This image already has the DB2 jdbc drive for use with Sqoop, Spark, or other required.

```
sqoop import --driver com.ibm.db2.jcc.DB2Driver --connect jdbc:db2://server:port/database --username XXXXX --password XXXXX --table schema.tablename --split-by idtable --target-dir /tmp/table_name
```
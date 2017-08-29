# Cloudera Quickstart 5.7.0

**Get this image**

```
$ docker pull sebagonella/zeppelin:0.7.2
```

**Build this image**

```
$ cd docker-cdh-zeppelin/zeppelin
$ docker build -t sebagonella/zeppelin:0.7.2 .
```

**Run a container**

```
$ docker run -d --name zeppelin -p 8282:8282 -p 8080:8080 sebagonella/zeppelin:0.7.2 /zeppelin/bin/zeppelin.sh
```

**Links**

Zeppelin  
http://localhost:8081  

Size docker image after build: 3.17GB

**Example - Using Impala interpreter**

The Apache Zeppelin image already has the Impala jdbc drive and a interpreter configured with it (jdbc type) to execute commands in the Impala of the Cloudera Quickstart enviropment.

```
%impala

select * from table_name;
```

**Example - Using Spark YARN mode**

This image has Zeppelin with Apache Spark configured and integrated with the Yarn of CDH.

Example - Save data on HDFS with PySpark

```
%pyspark

df = sc.parallelize((("a", 1), ("b", 2))).toDF()

df.write.save('hdfs://cloudera.quickstart:8020/tmp/TestHDFS5', mode='append')
```

**Zeppelin Interpreters**

* flink
* spark 
* impala (jdbc)
* psql
* livy
* hbase
* md
* sh
* alluxio
* pig
* bigquery
* cassandra
* lens
* hdfs
* jdbc
* ignite
* angular
* python
* kylin
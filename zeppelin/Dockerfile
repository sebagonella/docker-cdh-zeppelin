FROM apache/zeppelin:0.7.2

# Spark Version
ENV APACHE_SPARK_VERSION 1.6.0
ENV APACHE_HADOOP_VERSION 2.7.0

# Download jdbc Impala
# RUN curl http://nexus.sicoob.com.br/repository/big-data/impala_jdbc41.zip -o /zeppelin/interpreter/jdbc/impala_jdbc41.zip
# RUN unzip -o /zeppelin/interpreter/jdbc/impala_jdbc41.zip -d /zeppelin/interpreter/jdbc/

# hadoop
RUN curl -s http://www.eu.apache.org/dist/hadoop/common/hadoop-${APACHE_HADOOP_VERSION}/hadoop-${APACHE_HADOOP_VERSION}.tar.gz | tar -xz -C /usr/local/
RUN cd /usr/local && ln -s ./hadoop-${APACHE_HADOOP_VERSION} hadoop

ENV HADOOP_PREFIX=/usr/local/hadoop
ENV HADOOP_COMMON_HOME=/usr/local/hadoop
ENV HADOOP_HDFS_HOME=/usr/local/hadoop
ENV HADOOP_MAPRED_HOME=/usr/local/hadoop
ENV HADOOP_YARN_HOME=/usr/local/hadoop
ENV HADOOP_CONF_DIR=/usr/local/hadoop/etc/hadoop
ENV YARN_CONF_DIR=$HADOOP_PREFIX/etc/hadoop
ENV PATH=$PATH:/usr/local/hadoop/bin

# Adicionando configuracoes Zeppelin
ADD zeppelin-conf/zeppelin-env.sh /zeppelin/conf/zeppelin-env.sh
ADD zeppelin-conf/interpreter.json /zeppelin/conf/interpreter.json
ADD hadoop-conf/core-site.xml /usr/local/hadoop/etc/hadoop
ADD hadoop-conf/hdfs-site.xml /usr/local/hadoop/etc/hadoop
ADD hadoop-conf/mapred-site.xml /usr/local/hadoop/etc/hadoop
ADD hadoop-conf/yarn-site.xml /usr/local/hadoop/etc/hadoop

# Download e instalacao Spark
RUN cd /tmp && \
        wget -q http://d3kbcqa49mib13.cloudfront.net/spark-${APACHE_SPARK_VERSION}-bin-hadoop2.6.tgz && \
        echo "439fe7793e0725492d3d36448adcd1db38f438dd1392bffd556b58bb9a3a2601 *spark-${APACHE_SPARK_VERSION}-bin-hadoop2.6.tgz" | sha256sum -c - && \
        tar xzf spark-${APACHE_SPARK_VERSION}-bin-hadoop2.6.tgz -C /usr/local && \
        rm spark-${APACHE_SPARK_VERSION}-bin-hadoop2.6.tgz
RUN cd /usr/local && ln -s spark-${APACHE_SPARK_VERSION}-bin-hadoop2.6 spark


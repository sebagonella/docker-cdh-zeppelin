FROM apache/zeppelin:0.8.1

# Spark Version
ENV APACHE_SPARK_VERSION 2.4.3
ENV APACHE_HADOOP_VERSION 2.7.7

# Download jdbc Impala
ADD ./lib/impala_jdbc41.zip /zeppelin/interpreter/jdbc/impala_jdbc41.zip
ADD ./lib/db2jcc.jar /zeppelin/interpreter/jdbc/db2jcc.jar
RUN unzip -o /zeppelin/interpreter/jdbc/impala_jdbc41.zip -d /zeppelin/interpreter/jdbc/

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

# Adicionando configuracoes ao Zeppelin
ADD zeppelin-conf/zeppelin-env.sh /zeppelin/conf/zeppelin-env.sh
ADD zeppelin-conf/interpreter.json /zeppelin/conf/interpreter.json
ADD hadoop-conf/core-site.xml /usr/local/hadoop/etc/hadoop
ADD hadoop-conf/hdfs-site.xml /usr/local/hadoop/etc/hadoop
ADD hadoop-conf/mapred-site.xml /usr/local/hadoop/etc/hadoop
ADD hadoop-conf/yarn-site.xml /usr/local/hadoop/etc/hadoop

# Download e instalacao Spark
RUN cd /tmp && \
        wget -q https://www-eu.apache.org/dist/spark/spark-2.4.3/spark-${APACHE_SPARK_VERSION}-bin-hadoop2.7.tgz && \
        echo "e8b7f9e1dec868282cadcad81599038a22f48fb597d44af1b13fcc76b7dacd2a1caf431f95e394e1227066087e3ce6c2137c4abaf60c60076b78f959074ff2ad *spark-${APACHE_SPARK_VERSION}-bin-hadoop2.7.tgz" | sha512sum -c - && \
        tar xzf spark-${APACHE_SPARK_VERSION}-bin-hadoop2.7.tgz -C /usr/local && \
        rm spark-${APACHE_SPARK_VERSION}-bin-hadoop2.7.tgz
RUN cd /usr/local && ln -s spark-${APACHE_SPARK_VERSION}-bin-hadoop2.6 spark


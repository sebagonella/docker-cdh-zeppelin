FROM cloudera/quickstart

# Custom docker-quickstart - sem iniciar hbase e outros
ADD hadoop-conf/docker-quickstart /usr/bin/docker-quickstart
ADD hadoop-conf/docker-quickstart.original /usr/bin/docker-quickstart.original
RUN chmod 755 /usr/bin/docker-quickstart
RUN chmod 755 /usr/bin/docker-quickstart.original

RUN yum install -y wget

# JDBC DB2
# RUN curl http://nexus.sicoob.com.br/repository/big-data/db2jcc.jar -o /usr/share/java/db2jcc.jar

USER cloudera
WORKDIR /home/cloudera

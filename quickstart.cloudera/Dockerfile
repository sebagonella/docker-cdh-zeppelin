FROM cloudera/quickstart

# Custom docker-quickstart - sem iniciar hbase e outros
ADD hadoop-conf/docker-quickstart /usr/bin/docker-quickstart
ADD hadoop-conf/docker-quickstart.original /usr/bin/docker-quickstart.original
RUN chmod 755 /usr/bin/docker-quickstart
RUN chmod 755 /usr/bin/docker-quickstart.original

RUN yum install -y wget

# jdbc DB2


USER cloudera
WORKDIR /home/cloudera

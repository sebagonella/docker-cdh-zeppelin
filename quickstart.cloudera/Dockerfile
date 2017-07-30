FROM cloudera/quickstart:5.7.0-0-beta

# Custom docker-quickstart - sem iniciar hbase e outros
ADD hadoop-conf/docker-quickstart /usr/bin/docker-quickstart
ADD hadoop-conf/docker-quickstart.default /usr/bin/docker-quickstart.default
RUN chmod 755 /usr/bin/docker-quickstart
RUN chmod 755 /usr/bin/docker-quickstart.default

ADD hadoop-conf/start-single.sh /home/cloudera/start-single.sh
ADD hadoop-conf/stop-all.sh /home/cloudera/stop-all.sh
RUN chmod 755 /home/cloudera/start-single.sh
RUN chmod 755 /home/cloudera/stop-all.sh

# Install wget
RUN yum install -y wget

# JDBC DB2
ADD ./lib/db2jcc.jar /usr/share/java/db2jcc.jar

USER cloudera
WORKDIR /home/cloudera
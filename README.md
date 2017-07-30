# Docker - CDH e Zeppelin

Projeto para criação do ambiente integrado entre o Cloudera quickstart 5.7 e Apache Zeppelin 0.7.2 usando docker e docker-compose.

**Clone do projeto**

```
git clone https://github.com/sebagonella/docker-cdh-zeppelin.git
```

**Build do ambiente**

```
$ cd docker-cdh-zeppelin
$ docker-compose build
```

**Subindo o ambiente**

Subindo os dois containers

```
$ docker-compose up -d
```

Subindo apenas o Zeppelin

```
$ docker-compose up -d zeppelin
```

Subindo apenas o Cloudera

```
$ docker-compose up -d quickstart.cloudera
```

#### Cloudera quickstart

O container do Cloudera quickstart já está com o jdbc do DB2 para conexão das bases do Sicoob, principalmente para uso com Sqoop.

Tamanho da imagem após build: 6.34GB

**Exemplo de uso Sqoop com DB2**

No exemplo abaixo o Sqoop vai na base mnttbpp de monitoração, obtem os dados da tabela itemmonit e joga em formato csv na pasta /tmp/mnt_ti_itemmonit.

```
sqoop import --driver com.ibm.db2.jcc.DB2Driver --connect jdbc:db2://server:port/database --username XXXXX --password XXXXX --table schema.tablename --split-by iditem --target-dir /tmp/table_name
```

#### Apache Zeppelin

Já o container do Zeppelin está com o jdbc do Impala, bem como o interpreter Zeppelin (tipo jdbc) integrado e configurado ao CDH. Ou seja, para se usar o impala a partir do Zeppelin basta chamar o interpretador e executar a query.

Tamanho da imagem após build: 2.86GB

**Exemplo com Impala**

```
%impala

select * from table_name;
```

O container Zeppelin está com o Spark configurado e integrado ao Yarn do CDH, ou seja, as execuções do Spark (Spark, SparkR, PySpark, SparkSQL...) serão submetidas no Spark do CDH a partir do Yarn.

**Exemplo com PySpark**

```
df = sc.parallelize((("a", 1), ("b", 2))).toDF()

df.write.save('hdfs://cloudera.quickstart:8020/tmp/TestHDFS5', mode='append')
```

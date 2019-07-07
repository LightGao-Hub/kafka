# demo目录下的类均包含main函数，可以直接通过IDE运行（运行前修改参数指向自己的集群即可，详见代码注释）
# 也支持打包运行程序：

程序打包后可以使用如下命令启动生产者消费者程序：

#启动kafka:
先启动zookeeper命令：zookeeper-server-start.sh config/zookeeper.properties   我们这里使用的是kafka自带的zookeeper
再启动kafka: kafka-server-start.sh config/server.properties
创建主题：kafka-topics.sh  --create  --zookeeper  localhost:2181  --replication-factor  1  --partitions  1  --topic  gp-kafka-demo-topic
查看主题：kafka-topics.sh  --list  --zookeeper  localhost:2181

#生产者启动：因为需要kafka的JAR包所以跟的路径是：/home/hadoop/usr/kafka/libs/*

java -classpath ./demo_kafka-1.0-SNAPSHOT.jar:/home/hadoop/usr/kafka/libs/*:./ com.gupao.bd.kafka.demo.CustomerProducer

#消费者启动：

java -classpath ./demo_kafka-1.0-SNAPSHOT.jar:/home/hadoop/usr/kafka/libs/*:./ com.gupao.bd.kafka.demo.CustomerConsumer
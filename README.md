# spark_stream
Spark streaming application using kafka


1. Turn on zookeeper and Kafka using Ambari (HDP)
2. Create a Kafka topic using commmand-
bin/kafka-create-topic.sh --zookeeper 192.168.60.132:2181 --replica 1 --partition 1 --topic spark-test

Note- check the zookeeper host and port- Its 192.168.60.132 and 2181 for my HDP.

3.Verify the topic created using -
bin/kafka-list-topic.sh --zookeeper 192.168.60.132:2181

4. Create a producer using-
bin/kafka-console-producer.sh --broker-list 192.168.60.132:6667 --topic spark-test

Note- 6667 is port of kafka broker

5.Create a consumer using -
bin/kafka-console-consumer.sh --zookeeper 192.168.60.132:2181 --topic spark-test --from-beginning

6. Check the consumer group name( will be needed by Spark streaming application)-
bin/kafka-consumer-group.sh --list --zookeeper 192.168.60.132:2181

Note- It returned console-consumer-60135 for me

7. Start the spark streamin application using below arguments-
192.168.60.132:2181 console-consumer-60135 spark-test 3

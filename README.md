# 작성중 

# 공통
$ docker-compose up -d --build <br>
<br>
## kafka Zookeeper
$ wget https://archive.apache.org/dist/kafka/2.2.1/kafka_2.12-2.2.1.tgz<br>
$ tar xvf kafka_2.12-2.2.1.tgz<br>
$ cd kafka_2.12-2.2.1/bin<br>
$ ls<br>
<br>
$ docker-compose up -d --force-recreate --build<br>
<br>
<br>
< 클러스트 내 모든 토픽 리스트 조회 ><br>
$ ./kafka-topics.sh --list --bootstrap-server localhost:9092,localhost:9093,localhost:9094<br>
<br>
< 신규 토픽 생성 ><br>
$ ./kafka-topics.sh --create --zookeeper localhost:2181,localhost:2182,localhost:2183 --replication-factor 3 --partitions 1 --topic news<br>
<br>
< 토픽 정보 조회 ><br>
$ ./kafka-topics.sh --describe --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --topic news<br>
<br>
< 토픽에 메시지 발행 ><br>
$ ./kafka-console-producer.sh --broker-list localhost:9092,localhost:9093,localhost:9094 --topic news<br>
<br>
< 토픽 메시지 소비 ><br>
$ ./kafka-console-consumer.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --topic news --from-beginning<br>
<br>
< consumer group 으로 메시지 소비 ><br>
$ ./kafka-console-consumer.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --topic news --group news-group-1 --from-beginning<br>
<br>
< consumer group 정보 조회 ><br>
$ ./kafka-consumer-groups.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --list<br>
<br>
$ ./kafka-consumer-groups.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --group news-group-1 --describe<br>
<br>
< kafka_kafka-1_1 ><br>
1. 토픽 생성<br>
$ docker exec -t kafka_kafka-1_1 kafka-topics.sh --bootstrap-server localhost:9092 --create --topic testTopic<br>
2. 메시지 전송<br>
$ docker exec -it kafka_kafka-1_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092<br>
3. 메시지 수신<br>
$ docker exec -it kafka_kafka-1_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092<br>
<br>
< kafka_kafka-2_1 ><br>
1. 토픽 생성<br>
$ docker exec -t kafka_kafka-2_1 kafka-topics.sh --bootstrap-server loalhost:9092 --create --topic testTopic<br>
2. 메시지 전송<br>
$ docker exec -it kafka_kafka-2_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092<br>
3. 메시지 수신<br>
$ docker exec -it kafka_kafka-2_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092<br>
<br>
< kafka_kafka-3_1 ><br>
1. 토픽 생성<br>
$ docker exec -t kafka_kafka-3_1 kafka-topics.sh --bootstrap-server loalhost:9092 --create --topic testTopic<br>
2. 메시지 전송<br>
$ docker exec -it kafka_kafka-3_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092<br>
3. 메시지 수신<br>
$ docker exec -it kafka_kafka-3_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092<br>
<br>
<br>
## redis<br>
$ docker exec -it radis_redis-master_1 redis-cli<br>
<br>
$ info<br>
<br>
$ PING<br>
<br>
$ set test 123<br>
<br>
$ get test<br>

# 작성중 

# 공통
$ docker-compose up -d --build

## kafka Zookeeper
$ wget https://archive.apache.org/dist/kafka/2.2.1/kafka_2.12-2.2.1.tgz
$ tar xvf kafka_2.12-2.2.1.tgz
$ cd kafka_2.12-2.2.1/bin
$ ls

$ docker-compose up -d --force-recreate --build


< 클러스트 내 모든 토픽 리스트 조회 >
$ ./kafka-topics.sh --list --bootstrap-server localhost:9092,localhost:9093,localhost:9094

< 신규 토픽 생성 >
$ ./kafka-topics.sh --create --zookeeper localhost:2181,localhost:2182,localhost:2183 --replication-factor 3 --partitions 1 --topic news

< 토픽 정보 조회 >
$ ./kafka-topics.sh --describe --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --topic news

< 토픽에 메시지 발행 >
$ ./kafka-console-producer.sh --broker-list localhost:9092,localhost:9093,localhost:9094 --topic news

< 토픽 메시지 소비 >
$ ./kafka-console-consumer.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --topic news --from-beginning

< consumer group 으로 메시지 소비 >
$ ./kafka-console-consumer.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --topic news --group news-group-1 --from-beginning

< consumer group 정보 조회 >
$ ./kafka-consumer-groups.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --list

$ ./kafka-consumer-groups.sh --bootstrap-server localhost:9092,localhost:9093,localhost:9094 --group news-group-1 --describe

< kafka_kafka-1_1 >
1. 토픽 생성
$ docker exec -t kafka_kafka-1_1 kafka-topics.sh --bootstrap-server localhost:9092 --create --topic testTopic
2. 메시지 전송
$ docker exec -it kafka_kafka-1_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092
3. 메시지 수신
$ docker exec -it kafka_kafka-1_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092

< kafka_kafka-2_1 >
1. 토픽 생성
$ docker exec -t kafka_kafka-2_1 kafka-topics.sh --bootstrap-server loalhost:9092 --create --topic testTopic
2. 메시지 전송
$ docker exec -it kafka_kafka-2_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092
3. 메시지 수신
$ docker exec -it kafka_kafka-2_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092

< kafka_kafka-3_1 >
1. 토픽 생성
$ docker exec -t kafka_kafka-3_1 kafka-topics.sh --bootstrap-server loalhost:9092 --create --topic testTopic
2. 메시지 전송
$ docker exec -it kafka_kafka-3_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092
3. 메시지 수신
$ docker exec -it kafka_kafka-3_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092


## redis
$ docker exec -it radis_redis-master_1 redis-cli

$ info

$ PING

$ set test 123

$ get test

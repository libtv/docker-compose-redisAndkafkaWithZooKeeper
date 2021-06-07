# 작성중 
docker-compose up -d 

$ wget https://archive.apache.org/dist/kafka/2.2.1/kafka_2.12-2.2.1.tgz
$ tar xvf kafka_2.12-2.2.1.tgz
$ cd kafka_2.12-2.2.1/bin
$ ls
connect-distributed.sh              kafka-dump-log.sh                   kafka-topics.sh
connect-standalone.sh               kafka-log-dirs.sh                   kafka-verifiable-consumer.sh
kafka-acls.sh                       kafka-mirror-maker.sh               kafka-verifiable-producer.sh
kafka-broker-api-versions.sh        kafka-preferred-replica-election.sh offset.json
kafka-configs.sh                    kafka-producer-perf-test.sh         trogdor.sh
kafka-console-consumer.sh           kafka-reassign-partitions.sh        windows
kafka-console-producer.sh           kafka-replica-verification.sh       zookeeper-security-migration.sh
kafka-consumer-groups.sh            kafka-run-class.sh                  zookeeper-server-start.sh
kafka-consumer-perf-test.sh         kafka-server-start.sh               zookeeper-server-stop.sh
kafka-delegation-tokens.sh          kafka-server-stop.sh                zookeeper-shell.sh
kafka-delete-records.sh             kafka-streams-application-reset.sh

docker-compose up -d --force-recreate --build


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
docker exec -t kafka_kafka-1_1 kafka-topics.sh --bootstrap-server localhost:9092 --create --topic testTopic
2. 메시지 전송
docker exec -it kafka_kafka-1_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092
3. 메시지 수신
docker exec -it kafka_kafka-1_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092

< kafka_kafka-2_1 >
1. 토픽 생성
docker exec -t kafka_kafka-2_1 kafka-topics.sh --bootstrap-server loalhost:9092 --create --topic testTopic
2. 메시지 전송
docker exec -it kafka_kafka-2_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092
3. 메시지 수신
docker exec -it kafka_kafka-2_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092

< kafka_kafka-3_1 >
1. 토픽 생성
docker exec -t kafka_kafka-3_1 kafka-topics.sh --bootstrap-server loalhost:9092 --create --topic testTopic
2. 메시지 전송
docker exec -it kafka_kafka-3_1 kafka-console-producer.sh --topic testTopic --broker-list localhost:9092
3. 메시지 수신
docker exec -it kafka_kafka-3_1 kafka-console-consumer.sh --topic testTopic --bootstrap-server localhost:9092


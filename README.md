# Kafka Streams
<img src="https://user-images.githubusercontent.com/114554407/228961329-95175296-bd39-4365-baea-81ca8b234a43.jpeg" width="400"/>

### CDC (kafka Connect, Debezium, JDBC Sink Connector)
- Confluent 사의 JDBC Sink Connector 통해 구축
- Source DB : MySQL
- Source Connector: kafka Connect (Source Connector, Debezium)
- Target DB : Mysql, Oracle
- Sink Connector : kafka Connect (JDBC Sink Connector)
- [![](https://img.shields.io/badge/KarlaLog-000000?style=flat-square&logo=Tistory&logoColor=white)](https://karla.tistory.com/11?category=1125492)


### Kafka Streams
- strams_log 토픽 → stream() → to() → stream_log_copy 토픽
> stream() : 소스프로세서 <br> to() : 싱크프로세서
```bash
$ kafka-topics.sh --list --bootstrap-server localhost:9092

# 토픽 생성
$ kafka-topics.sh --create --bootstrap-server localhost:9092 --partitions 3 --topic stream_log

# 프로듀서, 컨슈머
$ kafka-console-producer.sh --bootstrap-server localhost:9092 --topic stream_log
$ kafka-console-consumer.sh --topic stream_log_copy --bootstrap-server localhost:9092 --from-beginning
```
<img src="https://user-images.githubusercontent.com/114554407/228963488-7bd289c8-f5d0-4d81-985c-e78db8e77b08.png" width="800"/>

<br>

### 스트림즈dsl filter()
- strams_log 토픽 → stream() → filter() → to() → stream_log_copy 토픽
> stream() : 소스프로세서 <br> filter(): 스트림프로세서 <br> to() : 싱크프로세서

```bash
$ kafka-console-consumer.sh --topic stream_log_filter --bootstrap-server localhost:9092 --from-beginning
```
<img src="https://user-images.githubusercontent.com/114554407/228963506-ef332308-faa2-44fe-8367-a16918c2cfb4.png" width="800"/>

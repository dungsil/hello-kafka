# Kafka 설치하기
**Kafka 2.2.1, zookeeper 3.4.13을 기준으로 작성하였습니다.**

테스트 용도로 로컬PC에 설치하는 걸 기준으로 작성, 추후 실무에서 사용하며 필요한 설정 등 내용 추가

## 다운로드
[Kafka 2.12](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.2.1/kafka_2.12-2.2.1.tgz) 다운로드 
및 압축 해제

## 서버시작
 - windows의 경우 windows 폴더의 배치파일을 bin으로 이동 시 
 ```classpath is missing``` 오류 발생
 
주키퍼:
```bash
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```

카프카:
```bash
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

## 토픽 생성하기
```bash
.\bin\windows\kafka-topics.bat --create --bootstrap-server localhost:9092 --topic [토픽 이름] --replication-factor [복제 갯수] --partitions [파티션 갯수]
```
 - ```replication-factor```은 주키퍼 수 만큼 설정?
 - ```partitions```는 컨슈머 갯수 만큼 설정?

## 생성된 토픽 확인 하기

토픽 목록 보기:
```bash
.\bin\windows\kafka-topics.bat --list --bootstrap-server localhost:9092
```

한 토픽에 대한 자세한 정보:
```bash
.\bin\windows\kafka-topics.bat --describe --bootstrap-server localhost:9092 --topic [토픽 이름]
```

## 메시지 생성하기
```bash
.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic [토픽 이름]
```
실행 후 나오는 ```>```에서 작성된 글을 엔터단위로 메시지를 보내는 거 같음
 - 샘플용 프로듀서?

## 메시지 처리하기
```bash
.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic [토픽 이름] --from-beginning
```
 - 샘플용 컨슈머?

## 출처
 - http://kafka.apache.org/documentation/

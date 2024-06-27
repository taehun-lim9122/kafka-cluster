# kafka-cluster

1. docker-compose 파일 실행 및 종료
```
# 전체 한번에 실행 시
docker-compose up -d

# 단일 컨테이너 실행 시
docker-compose up -d "컨테이너 이름"

# 컨테이너 종료
docker-compose down
```

## kafka 명령어

1. 컨테이너 로그 확인
```
docker-compose logs "컨테이너 이름"
```
2. 브로커 토픽 리스트 확인
```
docker exec -it {브로커 이름} kafka-topics --list --bootstrap-server {브로커 이름}:9092
```
3. 브로커 토픽 데이터 확인
```
docker exec -it {브로커 이름} kafka-console-consumer --bootstrap-server {브로커 이름}:9092 --topic "{토픽 이름}" --from-beginning
```
4. 브로커 토픽 내 파티션 확인
```
docker exec -it {브로커 이름} kafka-topics --bootstrap-server {브로커 이름}:9092 --describe --topic "토픽 이름"
```
5. 커넥터 리스트 확인
```
curl -X GET http://localhost:8083/connectors/
```
6. 커넥터 상태 확인
```
curl -X GET http://localhost:8083/connectors/"{커넥터 이름}"/status
```
7. 컨슈머 리스트 확인
```
docker exec -it {브로커 이름} kafka-consumer-groups --bootstrap-server {브로커 이름}:9092 --list
```
# LR Broker

사내 메신저 전용 메시지 브로커(Message Broker) 개발 프로젝트

## 📋 프로젝트 개요

LR Broker는 사내 메신저 시스템을 위한 전용 메시지 브로커입니다. 일반적인 메시지 큐 솔루션과 달리 메신저 서비스에 특화된 요구사항을 충족하도록 설계되었습니다.

## 🎯 프로젝트 목적

사내 메신저 시스템의 메세지 브로커로, **메시지 전달의 신뢰성**, **실시간성**, **오프라인 사용자 지원**, **읽음 처리** 의 기능을 담당하고 있습니다.

기존 상용 메시지 큐(Kafka, RabbitMQ 등)를 사용할 수도 있지만, 사내 메신저는 일반 메시징 플랫폼과 달리 비즈니스 요구에 맞는 경량화된 Broker로 개발되었습니다.

> **"메신저에 최적화된 고성능·고신뢰 메시지 전달 시스템을 직접 개발하기 위함"**

## 🎯 프로젝트 목표

본 프로젝트의 목표는 사내 메신저 서비스에서 필요한 전용 메시지 브로커(Message Broker)를 구축하여 메시지 전송의 핵심 기능을 안정적으로 제공하는 것입니다.

### 기능 요구 사항

#### 1. 메시지 신뢰성 극대화
- ACK 기반 무손실 메시지 전달
- 재전송 및 오프라인 사용자 메시지 관리

#### 2. 순서 보장(Message Ordering)
- Room(채팅방) 단위로 순서를 보장
- 단일 writer thread per room 방식

#### 3. 실시간 메시징 최적화
- WebSocket Gateway와 gRPC 스트리밍으로 실시간 low-latency 처리
- 메신저 특화 이벤트 연동(읽음, 입력중, 수정/삭제 등)

#### 4. 메신저 서비스를 위한 전용 스토리지 구축
- Append-only 파일 로그 기반 메시지 저장
- 서버 재시작 시 신속한 복구 및 오프라인 메시지 제공

#### 5. 장기적으로 확장 가능한 메시지 인프라 구축
- Room 기반 파티셔닝 → 향후 멀티 노드 샤딩 가능
- 메신저 외 실시간 이벤트 처리에도 재사용 가능

> **"메신저 서비스에 특화된 고성능, 무손실, 순서 보장 메시지 브로커 구축"**

## 🛠 기술 스택

- **Language**: Java 21
- **Build Tool**: Gradle 9.1.0
- **gRPC**: 1.60.0
  - grpc-netty-shaded
  - grpc-protobuf
  - grpc-stub
- **Logging**: SLF4J 2.0.9, Logback 1.4.11
- **JSON**: Jackson Databind 2.15.2
- **Testing**: JUnit Jupiter 5.10.1, Mockito 5.7.0


## 시작하기

### 사전 요구사항

- Java 21 이상
- Gradle 9.1.0 이상 (또는 Gradle Wrapper 사용)

### 빌드

```bash
# Gradle Wrapper 사용
./gradlew build

# 또는 시스템 Gradle 사용
gradle build
```

### 실행

```bash
# 애플리케이션 실행
./gradlew run

# 또는 빌드된 JAR 실행
./gradlew build
java -jar build/libs/lr-broker-1.0.0-SNAPSHOT.jar
```

### 테스트

```bash
./gradlew test
```

## 📝 기여하기

프로젝트에 기여하고 싶으시다면 [CONTRIBUTING.md](.github/CONTRIBUTING.md)를 참고해주세요.

## 📄 라이선스

[라이선스 정보를 추가해주세요]

## 🔗 관련 링크

- [이슈 템플릿](.github/ISSUE_TEMPLATE/)
- [Pull Request 템플릿](.github/pull_request_template.md)


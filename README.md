# KIM JISEOP | Backend Portfolio

> 기능 목록보다,  
> 운영 환경에서 문제가 되기 쉬운 **상태 전이, 외부 연동, 재시도, 복구 가능성**을  
> 어떤 Backend 구조로 풀어냈는지 정리한 포트폴리오입니다.

## Portfolio Direction

이 포트폴리오는 실무에서 자주 마주치는 운영형 Backend 문제를  
프로젝트 단위로 재구성한 자료입니다.

현재 대표 프로젝트는 `commerce-orchestration-backend`이며,  
주문 이후 payment · settlement · notification · outbox 흐름을  
상태 전이와 실패 복구 중심으로 설계했습니다.

## What I Solve

- 외부 Provider 연동에서 복잡해지는 요청 / 응답 / 예외 흐름
- 상태 전이와 최종 정합성이 중요한 운영형 로직
- Batch / Scheduler / Daemon의 실행 제어와 재시도
- Redis / PostgreSQL / Messaging 간 역할 분리와 복구 가능성
- 서버 기준 검증, 추적, 상태 연결 구조
- 레거시 구조 분석과 점진적 리빌딩 / 리팩토링

## Positioning

- **Role**: Backend Developer
- **Focus**: Operational Stability / State Management / External Integration / Recovery
- **Main Stack**: Java, Spring Boot, MyBatis, Oracle
- **Also Used**: Redis, PostgreSQL, Docker, JPA, QueryDSL, Kafka

## Featured Projects

### [commerce-orchestration-backend](https://github.com/Gseobi/commerce-orchestration-backend)

주문 이후 payment · settlement · notification · outbox 흐름을  
orchestration, explicit state transition, compensation, retry / dead-letter, admin recovery 관점으로 설계한 프로젝트입니다.

`Transaction Flow` · `Explicit State` · `Outbox` · `Recovery`

---

### [provider-integration-gateway](https://github.com/Gseobi/provider-integration-gateway)

다수 Provider / PG 연동 환경에서  
Provider 선택, 요청 구성, 응답 표준화, 예외 처리 책임을 Gateway 계층으로 분리한 프로젝트입니다.

`External Integration` · `Strategy Pattern` · `Response Standardization`

---

### [ops-scheduler-batch-jobs](https://github.com/Gseobi/ops-scheduler-batch-jobs)

Scheduler / Batch 작업에서 발생할 수 있는  
중복 실행, 실패 재시도, 실행 이력 확인 문제를 운영 관점에서 구조화한 프로젝트입니다.

`Scheduler` · `Retry Flow` · `Execution Control`

---

### [realtime-caching-gateway](https://github.com/Gseobi/realtime-caching-gateway)

Redis를 실시간 처리 계층으로, PostgreSQL을 fallback 및 최종 영속 계층으로 분리해  
응답 속도와 복구 가능성을 함께 고려한 프로젝트입니다.

`Cache / Data Flow` · `Fallback Recovery` · `Consistency`

---

### [deferred-deeplink-backend](https://github.com/Gseobi/deferred-deeplink-backend)

설치 전 / 후가 분리된 Deferred Deeplink 흐름에서  
서버 기준 추적, 검증, 상태 연결 구조를 설계한 프로젝트입니다.

`Server-side Validation` · `Click Tracking` · `State Consistency`

---

### [java-socket-daemon-springboot](https://github.com/Gseobi/java-socket-daemon-springboot)

DB Polling, 암·복호화, Socket 송수신, 결과 반영 흐름을 분리해  
장기 실행 Provider 연동 구조를 설계한 프로젝트입니다.

`Socket Daemon` · `Encryption Flow` · `Timeout / Retry`

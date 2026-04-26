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

#### Related Notes

- [커머스 주문 이후 흐름을 상태 전이와 Orchestration으로 설계하기](https://velog.io/@wsx2386/%EC%BB%A4%EB%A8%B8%EC%8A%A4-%EC%A3%BC%EB%AC%B8-%EC%9D%B4%ED%9B%84-%ED%9D%90%EB%A6%84%EC%9D%84-%EC%83%81%ED%83%9C-%EC%A0%84%EC%9D%B4%EC%99%80-Orchestration%EC%9C%BC%EB%A1%9C-%EC%84%A4%EA%B3%84%ED%95%98%EA%B8%B0)
  
  주문 이후 결제, 정산, 알림, Outbox 흐름을 상태 전이와 실패 분기 중심으로 정리했습니다.

- [Outbox 재처리 구조에서 중복 처리와 멱등성을 어떻게 방어할까](https://velog.io/@wsx2386/Outbox-%EC%9E%AC%EC%B2%98%EB%A6%AC-%EA%B5%AC%EC%A1%B0%EC%97%90%EC%84%9C-%EC%A4%91%EB%B3%B5-%EC%B2%98%EB%A6%AC%EC%99%80-%EB%A9%B1%EB%93%B1%EC%84%B1%EC%9D%84-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%B0%A9%EC%96%B4%ED%95%A0%EA%B9%8C)
  
  재처리 가능한 구조에서 발생할 수 있는 중복 요청과 동시 실행 문제를 `paymentRequestId`, `PROCESSING` claim, Outbox publisher adapter로 방어한 내용을 정리했습니다.
  
---

### [provider-integration-gateway](https://github.com/Gseobi/provider-integration-gateway)

다수 Provider / PG 연동 환경에서  
Provider 선택, 요청 구성, 응답 표준화, 예외 처리 책임을 Gateway 계층으로 분리한 프로젝트입니다.

`External Integration` · `Strategy Pattern` · `Response Standardization`

#### Related Notes

- [여러 외부 Provider를 연동하는 Backend는 왜 Gateway 구조가 필요할까](https://velog.io/@wsx2386/%EC%97%AC%EB%9F%AC-%EC%99%B8%EB%B6%80-Provider%EB%A5%BC-%EC%97%B0%EB%8F%99%ED%95%98%EB%8A%94-Backend%EB%8A%94-%EC%99%9C-Gateway-%EA%B5%AC%EC%A1%B0%EA%B0%80-%ED%95%84%EC%9A%94%ED%95%A0%EA%B9%8C)

---

### [ops-scheduler-batch-jobs](https://github.com/Gseobi/ops-scheduler-batch-jobs)

Scheduler / Batch 작업에서 발생할 수 있는  
중복 실행, 실패 재시도, 실행 이력 확인 문제를 운영 관점에서 구조화한 프로젝트입니다.

`Scheduler` · `Retry Flow` · `Execution Control`

#### Related Notes

- [이중화 환경에서 Scheduler와 Batch를 어떻게 안전하게 실행할 것인가](https://velog.io/@wsx2386/%EC%9D%B4%EC%A4%91%ED%99%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-Scheduler%EC%99%80-Batch%EB%A5%BC-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%95%88%EC%A0%84%ED%95%98%EA%B2%8C-%EC%8B%A4%ED%96%89%ED%95%A0-%EA%B2%83%EC%9D%B8%EA%B0%80)

---

### [realtime-caching-gateway](https://github.com/Gseobi/realtime-caching-gateway)

Redis를 실시간 처리 계층으로, PostgreSQL을 fallback 및 최종 영속 계층으로 분리해  
응답 속도와 복구 가능성을 함께 고려한 프로젝트입니다.

`Cache / Data Flow` · `Fallback Recovery` · `Consistency`

#### Related Notes

- [Redis 캐시는 hit보다 miss 이후 복구 전략이 더 중요하다](https://velog.io/@wsx2386/%EC%BA%90%EC%8B%9C%EB%8A%94-hit%EB%B3%B4%EB%8B%A4-miss-%EC%9D%B4%ED%9B%84-%EB%B3%B5%EA%B5%AC-%EC%A0%84%EB%9E%B5%EC%9D%B4-%EB%8D%94-%EC%A4%91%EC%9A%94%ED%95%98%EB%8B%A4)

---

### [deferred-deeplink-backend](https://github.com/Gseobi/deferred-deeplink-backend)

설치 전 / 후가 분리된 Deferred Deeplink 흐름에서  
서버 기준 추적, 검증, 상태 연결 구조를 설계한 프로젝트입니다.

`Server-side Validation` · `Click Tracking` · `State Consistency`

#### Related Notes

- [설치 전후가 끊기는 환경에서 Deferred Deeplink를 서버 기준으로 검증하는 구조](https://velog.io/@wsx2386/%EC%84%A4%EC%B9%98-%EC%A0%84%ED%9B%84%EA%B0%80-%EB%81%8A%EA%B8%B0%EB%8A%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-Deferred-Deeplink%EB%A5%BC-%EC%84%9C%EB%B2%84-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-%EA%B2%80%EC%A6%9D%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)

---

### [java-socket-daemon-springboot](https://github.com/Gseobi/java-socket-daemon-springboot)

DB Polling, 암·복호화, Socket 송수신, 결과 반영 흐름을 분리해  
장기 실행 Provider 연동 구조를 설계한 프로젝트입니다.

`Socket Daemon` · `Encryption Flow` · `Timeout / Retry`

#### Related Notes

- [장기 실행 Socket Daemon을 운영 가능한 구조로 만들기 위해 고려한 것들](https://velog.io/@wsx2386/%EC%9E%A5%EA%B8%B0-%EC%8B%A4%ED%96%89-Socket-Daemon%EC%9D%84-%EC%9A%B4%EC%98%81-%EA%B0%80%EB%8A%A5%ED%95%9C-%EA%B5%AC%EC%A1%B0%EB%A1%9C-%EB%A7%8C%EB%93%A4%EA%B8%B0-%EC%9C%84%ED%95%B4-%EA%B3%A0%EB%A0%A4%ED%95%9C-%EA%B2%83%EB%93%A4)

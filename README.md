# KIM JISEOP | Portfolio

> 기능 목록보다,  
> 운영 환경에서 실제로 문제가 되는 지점을  
> 어떤 구조로 풀어냈는지 보여주기 위해 정리한 Backend Portfolio입니다.

## What I Solve

- 외부 시스템 / Provider 연동에서 복잡해지는 분기와 예외 흐름
- 상태 전이와 최종 정합성이 중요한 운영형 로직
- 캐시, 메시징, DB 간 역할 분리와 복구 가능성
- 배치 / 스케줄러 / 콜백 흐름의 실행 제어와 재시도
- 서버 기준 검증과 추적이 필요한 흐름 설계
- 레거시 구조 분석과 점진적 리빌딩 / 리팩토링

## Positioning

- **Role**: Backend Developer
- **Focus**: Operational Stability / State Management / External Integration / Recovery
- **Main Stack**: Java, Spring Boot, MyBatis, Oracle
- **Also Used**: Redis, PostgreSQL, Docker, JPA, QueryDSL

## Featured Projects

### [commerce-orchestration-backend](https://github.com/Gseobi/commerce-orchestration-backend)
주문 이후 payment · settlement · notification · outbox 흐름을  
orchestration, explicit state transition, compensation, admin recovery 관점으로 정리한 프로젝트

`Transaction Flow` · `Explicit State` · `Recovery`

### [provider-integration-gateway](https://github.com/Gseobi/provider-integration-gateway)
다수 Provider / PG 연동 환경에서  
Provider 선택, 요청 구성, 응답 표준화 책임을 게이트웨이로 분리한 프로젝트

`External Integration` · `Strategy Pattern` · `Response Standardization`

### [ops-scheduler-batch-jobs](https://github.com/Gseobi/ops-scheduler-batch-jobs)
중복 실행 제어, 재시도 흐름, 운영 확인 포인트를 구조화한 Scheduler / Batch 프로젝트

`Scheduler` · `Retry Flow` · `Execution Control`

### [realtime-caching-gateway](https://github.com/Gseobi/realtime-caching-gateway)
Redis를 실시간 처리 계층으로, PostgreSQL을 fallback 및 최종 영속 계층으로 분리해  
응답 속도와 복구 가능성을 함께 고려한 프로젝트

`Cache / Data Flow` · `Fallback Recovery` · `Consistency`

### [deferred-deeplink-backend](https://github.com/Gseobi/deferred-deeplink-backend)
설치 전/후가 분리된 흐름에서  
서버 기준 추적, 검증, 상태 연결 구조를 설계한 프로젝트

`Server-side Validation` · `Click Tracking` · `State Consistency`

### [java-socket-daemon-springboot](https://github.com/Gseobi/java-socket-daemon-springboot)
DB Polling, 암·복호화, Socket 송수신, 결과 반영 흐름을 분리해  
장기 실행 Provider 연동 구조를 설계한 프로젝트

`Socket Daemon` · `Timeout / Retry` · `Execution Flow`

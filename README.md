# KIM JISEOP | Portfolio

실서비스 API 운영 경험을 바탕으로,  
외부 연동 · 상태 관리 · 정합성 · 배치/스케줄링처럼 운영 민감도가 높은  
백엔드 문제를 운영 관점에서 설계하고 개선해온 Java Backend Developer의 대표 프로젝트 포트폴리오입니다.

이 문서는 기능 목록보다,  
운영 민감도가 높은 Backend 문제를 어떤 구조로 풀어냈는지 보여주는 데 초점을 둡니다.

<br/>

## About This Portfolio

저는 단순히 동작하는 기능을 구현하는 것보다,  
운영 환경에서 실제로 문제가 되는 지점을 구조적으로 풀어내는 방식에 더 관심이 있습니다.

실무에서는 통합 플랫폼 서버와 사내 공통 External API Gateway를 중심으로 작업해왔고,  
외부 연동, 상태 관리, 정합성, 복구 가능성이 중요한 문제를 주로 다뤄왔습니다.

이 경험을 바탕으로 포트폴리오 프로젝트 역시  
예제형 CRUD보다 **운영형 구조 설계**가 드러나도록 구성했습니다.

<br/>

## Positioning

- **Role**: Java Backend Developer
- **Focus**: Operational Stability / State Management / External Integration / Batch-Scheduler / Consistency
- **Main Stack**: Java, Spring Boot, MyBatis, Oracle
- **Working Knowledge**: Redis, PostgreSQL, Docker, JPA, QueryDSL

<br/>

## What I Solve

주로 아래와 같은 문제를 중요하게 봅니다.

- 외부 시스템 / Provider 연동 시 비대해지는 분기와 예외 흐름
- 상태 전이와 최종 정합성이 중요한 운영형 로직 설계
- 캐시, 메시징, DB 간 역할 분리와 복구 가능성
- 배치 / 스케줄러 / 콜백 프로세스의 실행 제어와 재시도
- 서버 기준 검증과 추적이 필요한 흐름 설계
- 레거시 구조 분석과 점진적 리빌딩 / 리팩토링

<br/>

## Featured Projects

### 1. [commerce-orchestration-backend](https://github.com/Gseobi/commerce-orchestration-backend)

**Summary**  
주문 이후 payment · settlement · notification 흐름을 orchestration, outbox, compensation, admin recovery 관점으로 설계한 Backend 프로젝트

**Focus**
- `CommerceOrchestrationService` 중심의 흐름 제어와 domain 책임 분리
- settlement failure와 notification failure의 보상 / 복구 정책 분리
- outbox retry / dead-letter / admin reprocessing 구조 설계

**Why It Matters**  
단순 주문 API 구현이 아니라,  
**주문 이후 후속 처리 흐름을 운영 가능한 구조로 제어하고 실패 시에도 복구 가능한 Backend 구조를 어떻게 설계할 것인가**를 보여주기 위한 프로젝트입니다.

<br/>

### 2. [provider-integration-gateway](https://github.com/Gseobi/provider-integration-gateway)

**Summary**  
다수 Provider / PG 연동 환경에서 Provider 선택, 요청 구성, 응답 표준화를 Backend 게이트웨이로 모아 설계한 프로젝트

**Focus**
- Provider별 구현 책임 분리
- 공통 응답 구조 표준화
- 확장 가능한 라우팅 구조 설계

**Why It Matters**  
단순 연동 기능이 아니라,  
**외부 연동 구조를 제어 가능한 형태로 유지하는 방식**을 보여주기 위한 프로젝트입니다.

<br/>

### 3. [ops-scheduler-batch-jobs](https://github.com/Gseobi/ops-scheduler-batch-jobs)

**Summary**  
운영형 배치에서 필요한 중복 실행 제어, 재시도 흐름, 운영 가시성을 구조화한 Scheduler / Batch 프로젝트

**Focus**
- 시간 분산 실행과 실행 제어 구조 분리
- 실패 시 재시도 흐름 설계
- 운영 로그 / 상태 확인 포인트 정리

**Why It Matters**  
단순 스케줄 등록이 아니라,  
**운영 가능한 배치 구조를 어떻게 만들 것인가**에 초점을 둔 프로젝트입니다.

<br/>

### 4. [java-socket-daemon-springboot](https://github.com/Gseobi/java-socket-daemon-springboot)

**Summary**  
DB 기반 작업 Polling, 암·복호화, Socket 송수신, 결과 반영 흐름을 분리해 장기 실행 Provider 연동 Daemon 구조를 설계한 프로젝트

**Focus**
- Polling 기반 작업 처리와 결과 반영 구조
- Provider별 설정 분리
- timeout / retry / 예외 흐름 설계

**Why It Matters**  
단순 Socket 연동이 아니라,  
**운영 가능한 장기 실행 Daemon 구조**를 보여주기 위한 프로젝트입니다.

<br/>

### 5. [realtime-caching-gateway](https://github.com/Gseobi/realtime-caching-gateway)

**Summary**  
Redis를 실시간 처리 및 캐시 계층으로 활용하고 PostgreSQL fallback / synchronization 구조로 성능과 복구 가능성을 함께 고려한 프로젝트

**Focus**
- Redis를 처리 계층으로 확장
- PostgreSQL fallback / synchronization 구조 설계
- 캐시 적중률뿐 아니라 복구 가능성과 정합성 고려

**Why It Matters**  
캐시를 써서 빠르게 만드는 것보다,  
**빠르게 처리하면서도 장애 시 복구 가능한 구조**를 보여주는 프로젝트입니다.

<br/>

### 6. [deferred-deeplink-backend](https://github.com/Gseobi/deferred-deeplink-backend)

**Summary**  
광고 클릭 이후 앱 설치 전/후가 분리되는 흐름에서 서버 기준 추적, 검증, 상태 연결 구조를 설계한 프로젝트

**Focus**
- 설치 전/후 흐름을 서버 기준으로 연결
- 위변조 방지와 유입 식별 검증
- 추적 / 귀속 흐름의 정합성 확보

**Why It Matters**  
단순 링크 생성이 아니라,  
**시간적으로 분리된 사용자 흐름을 서버 기준으로 검증하고 연결하는 방식**을 보여주기 위한 프로젝트입니다.

<br/>

## Practical Experience Summary

실무에서는 아래와 같은 흐름을 중심으로 작업해왔습니다.

- 통합 플랫폼 서버 및 External API Gateway 설계 / 개발 / 운영 / 유지보수
- 작업 설계 → 프로세스 설계 → 파라미터 명세 → 개발 → 테스트 → 배포
- 충전, 결제, 가입자 조회, Mail, 국제 SMS, Push 영역의 API 작업
- Daemon, Scheduler, Callback API, Callback Daemon 설계 및 유지보수
- 외부 연동 업체와의 협의, 테스트, 상용 적용 직접 수행
- 레거시 PHP / Java 구조 분석 및 Spring Boot / Gradle 기반 리빌딩
- 운영 이슈 원인 분석, 예외 흐름 보완, 재시도 / 복구 구조 개선

<br/>

## Engineering Background

이전에는 자동화 설비 소프트웨어 엔지니어로 근무하며  
래더 프로그램과 Script 기반 제어 로직을 다뤘습니다.

설비 프로그램 제작, 현장 셋업, 개조, 유지보수, 이슈 대응까지 전 과정을 수행했으며,  
이 경험은 현재 백엔드 개발에서도 **운영 안정성, 현장 문제 해결, 시스템 흐름 중심 사고**로 이어지고 있습니다.

<br/>

## What These Projects Show

이 포트폴리오의 대표 프로젝트들은 공통적으로 아래 역량을 보여주기 위해 구성했습니다.

- 운영 민감도가 높은 Backend 문제를 구조적으로 바라보는 관점
- 상태 관리와 최종 정합성을 고려한 설계
- 실패 시 복구 가능성과 제어 가능성을 우선하는 방식
- 외부 연동에서 분기, 응답, 예외를 다루는 구조화 능력
- 배치 / 스케줄러 / 캐시 / 검증 흐름을 운영 관점에서 설계하는 능력
- 레거시를 분석하고 현대적인 구조로 재구성하는 문제 해결 방식

<br/>

## Links

- **GitHub**: [github.com/Gseobi](https://github.com/Gseobi)
- **Velog**: [velog.io/@wsx2386/posts](https://velog.io/@wsx2386/posts)
- **LinkedIn**: [linkedin.com/in/jiseop-kim-3983813b9](https://www.linkedin.com/in/jiseop-kim-3983813b9/)
- **Email**: [wsx2386@naver.com](mailto:wsx2386@naver.com)

<br/>

## Notes

이 문서는 채용공고별 제출용 포트폴리오가 아니라,  
GitHub 메인 프로필에서 공통적으로 연결할 수 있는 **공개용 Portfolio** 기준으로 작성했습니다.

지원 회사별 제출 문서는 별도로 관리하고,  
이 문서는 공개용 대표 버전으로 유지합니다.

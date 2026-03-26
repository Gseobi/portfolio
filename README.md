# KIM JISEOP | Portfolio

실서비스 앱이 호출하는 **통합 플랫폼 서버**와  
사내 공통 기능으로 활용되는 **External API Gateway**의 설계, 개발, 운영, 유지보수를 중심으로 경험을 쌓아온  
**Java Backend Developer**의 대표 프로젝트 포트폴리오입니다.

이 문서는 기능 목록을 나열하기보다,  
**어떤 운영형 백엔드 문제를 어떤 구조로 풀어냈는가**를 빠르게 보여주는 것을 목표로 합니다.

</br>

## About This Portfolio

저는 단순히 동작하는 기능을 구현하는 것보다,  
운영 환경에서 실제로 문제가 되는 지점을 구조적으로 풀어내는 방식에 더 관심이 있습니다.

실무에서는 회사 앱서비스가 호출하는 API들을 통합한 **플랫폼 서버**와,  
사내 공통 기능으로 활용되는 **External API 연동 Gateway**를 중심으로 작업해왔습니다.

또한 백엔드 파트 전임 1인으로서  
작업 요청이 들어오면 단순 구현만 수행하는 것이 아니라,  
**작업 설계, 프로세스 설계, 파라미터 명세 정리, 개발, 테스트, 배포**까지 직접 수행해왔습니다.

외부 연동 업무에서는 업체와의 미팅, 연동 방식 협의, 테스트, 상용 환경 적용까지 단독으로 진행했으며,  
일부 레거시 PHP / Java 시스템은 **Spring Boot / Gradle 형태로 리빌딩**하며 구조 개선을 진행했습니다.

이 경험을 바탕으로 포트폴리오 프로젝트 역시  
예제형 CRUD보다 **운영 안정성, 외부 연동, 상태 관리, 정합성, 복구 가능성**이 드러나도록 재구성했습니다.

</br>

## Positioning

- **Role**: Java Backend Developer
- **Focus**: Operational Stability / State Management / External Integration / Consistency
- **Main Stack**: Java, Spring Boot, MyBatis, Oracle
- **Working Knowledge**: Redis, PostgreSQL, Docker, JPA, QueryDSL

</br>

## What I Solve

주로 아래와 같은 문제를 중요하게 봅니다.

- 외부 시스템 / Provider 연동 시 비대해지는 분기와 예외 흐름
- 캐시, 메시징, DB 간 역할 분리와 복구 가능성
- 배치 / 스케줄러 / 콜백 프로세스의 실행 제어, 중복 실행 방지, 재시도
- 설치 전/후처럼 흐름이 분리되는 상황에서의 서버 기준 검증과 정합성
- 레거시 구조를 이해하고 운영 리스크를 낮추는 방향의 리빌딩과 점진적 리팩토링

</br>

## Featured Projects

### 1. [realtime-caching-gateway](https://github.com/Gseobi/realtime-caching-gateway)

#### One-line Summary
Redis를 실시간 처리 및 캐시 계층으로 활용하고 PostgreSQL fallback / synchronization 구조로 성능과 복구 가능성을 함께 고려한 프로젝트

#### Problem
실시간 메시지 처리와 빠른 응답을 위해 캐시를 도입하더라도,  
캐시 장애나 데이터 유실 상황에서 복구 전략과 최종 정합성까지 고려하지 않으면 운영 리스크가 커질 수 있습니다.

#### What I Focused On
- Redis를 단순 캐시가 아니라 처리 계층으로 확장
- PostgreSQL fallback / synchronization 구조 설계
- 캐시 적중률뿐 아니라 복구 가능성과 정합성 고려
- 처리 성능과 데이터 안정성 사이의 균형 설계

#### Why It Matters
이 프로젝트는 “캐시를 써서 빠르게 만들기”보다  
**빠르게 처리하면서도 장애 시 복구 가능한 구조를 어떻게 만들 것인가**를 보여줍니다.

</br>

### 2. [provider-integration-gateway](https://github.com/Gseobi/provider-integration-gateway)

#### One-line Summary
다수 Provider / PG 연동 환경에서 Provider 선택, 요청 구성, 응답 표준화를 Backend 게이트웨이로 모아 설계한 프로젝트

#### Problem
외부 시스템이 늘어날수록 호출부에 Provider별 분기와 예외 처리가 퍼지기 쉽고,  
응답 구조도 제각각이라 서비스 로직이 빠르게 비대해질 수 있습니다.

#### What I Focused On
- Provider별 구현 책임 분리
- 공통 응답 구조 표준화
- 확장 가능한 라우팅 구조
- 호출부 복잡도 감소와 유지보수성 확보

#### Why It Matters
이 프로젝트는 단순 연동 기능보다  
**외부 연동 구조를 어떻게 제어 가능한 형태로 유지할 것인가**에 초점을 두고 있습니다.

</br>

### 3. [ops-scheduler-batch-jobs](https://github.com/Gseobi/ops-scheduler-batch-jobs)

#### One-line Summary
운영형 배치에서 필요한 중복 실행 제어, 재시도 흐름, 운영 가시성을 구조화한 스케줄러/배치 프로젝트

#### Problem
배치나 스케줄러는 단순히 정해진 시간에 실행되는 기능처럼 보이지만,  
운영 환경에서는 중복 실행, 실패 후 재처리, 실행 이력 추적, 외부 연동 실패 대응이 더 중요해집니다.

#### What I Focused On
- 시간 분산 실행과 실행 제어 구조 분리
- 실패 시 재시도 흐름 설계
- 운영 로그 / 상태 확인 포인트 정리
- 실행 안정성과 운영 제어 가능성 강화

#### Why It Matters
이 프로젝트는 단순 스케줄 등록이 아니라  
**운영 가능한 배치 구조를 어떻게 만들 것인가**에 초점을 둔 프로젝트입니다.

</br>

### 4. [deferred-deeplink-backend](https://github.com/Gseobi/deferred-deeplink-backend)

#### One-line Summary
광고 클릭 이후 앱 설치 전/후가 분리되는 흐름에서 서버 기준 추적, 검증, 상태 연결 구조를 설계한 프로젝트

#### Problem
광고 유입, 앱 설치, 최초 실행이 시간적으로 분리되는 구조에서는  
단순 딥링크 생성만으로는 유입 식별, 검증, 귀속 처리의 정합성을 안정적으로 보장하기 어렵습니다.

#### What I Focused On
- 설치 전/후 흐름을 서버 기준으로 연결
- 위변조 방지와 유입 식별 검증
- Click ID 및 검증 정보 관리
- 추적/귀속 흐름의 정합성 확보

#### Why It Matters
이 프로젝트는 단순 링크 생성 기능이 아니라  
**시간적으로 분리된 사용자 흐름을 서버 기준으로 어떻게 검증하고 연결할 것인가**를 보여줍니다.

</br>

## Practical Experience Summary

실무에서는 아래와 같은 흐름을 중심으로 작업해왔습니다.

- 회사 앱서비스가 호출하는 API들을 통합한 **플랫폼 서버** 설계 / 개발 / 운영 / 유지보수
- 사내 공통 기능으로 활용되는 **External API 연동 Gateway** 설계 / 개발 / 운영 / 유지보수
- 작업 요청 수신 이후 **작업 설계 → 프로세스 설계 → 파라미터 명세 정리 → 개발 → 테스트 → 배포**
- 충전, 결제, 가입자 조회, Mail, 국제 SMS, Push 영역의 API 작업 수행
- Daemon, Scheduler, Callback API, Callback Daemon 설계 및 유지보수
- 외부 연동 업체와의 미팅, 연동 협의, 테스트, 상용 환경 적용 단독 수행
- 레거시 PHP / Java 구조 분석 및 Spring Boot / Gradle 기반 리빌딩
- 운영 중 발생하는 이슈에 대한 원인 분석, 예외 흐름 보완, 재시도 / 복구 구조 개선

이 경험을 바탕으로,  
포트폴리오 프로젝트 또한 단순 예제 구현보다 **운영형 구조 설계**를 보여주는 방향으로 재구성했습니다.

</br>

## Engineering Background

이전에는 자동화 설비 소프트웨어 엔지니어로 근무하며  
래더 프로그램과 Script 기반 제어 로직을 다뤘습니다.

설비 프로그램 제작, 현장 셋업, 개조, 유지보수, 이슈 대응까지 전 과정을 수행했으며,  
이 경험은 현재 백엔드 개발에서도 **운영 안정성, 현장 문제 해결, 시스템 흐름 중심 사고**로 이어지고 있습니다.

</br>

## What These Projects Show

이 포트폴리오의 대표 프로젝트들은 공통적으로 아래 역량을 보여주기 위해 구성했습니다.

- 운영 민감도가 높은 Backend 문제를 구조적으로 바라보는 관점
- 상태 관리와 최종 정합성을 고려한 설계
- 실패 시 복구 가능성과 제어 가능성을 우선하는 방식
- 외부 시스템 연동에서 분기, 응답, 예외를 다루는 구조화 능력
- 배치 / 스케줄러 / 캐시 / 검증 흐름을 운영 관점에서 설계하는 능력
- 레거시를 분석하고 현대적인 구조로 재구성하는 문제 해결 방식

</br>

## Links

- **GitHub**: [github.com/Gseobi](https://github.com/Gseobi)
- **LinkedIn**: [linkedin.com/in/jiseop-kim-3983813b9](https://www.linkedin.com/in/jiseop-kim-3983813b9/)
- **Email**: [wsx2386@naver.com](mailto:wsx2386@naver.com)

</br>

## Notes

이 문서는 채용공고별 제출용 포트폴리오가 아니라,  
GitHub 메인 프로필에서 공통적으로 연결할 수 있는 **공개용 Portfolio** 기준으로 작성했습니다.

지원 회사별로 강조 포인트를 조정한 제출용 문서는 별도로 관리하고,  
이 문서는 공개용 대표 버전으로 유지하는 것을 기준으로 합니다.

# 송정기

공공 모바일 서비스(사용자 약 20만 명) 백엔드 개발·운영 1년 7개월

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white) ![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=flat-square&logo=rabbitmq&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

### [Locus](https://github.com/thdwjdrl401/locus) · 디바이스 위치·상태 데이터 수집 및 모니터링 서버

<img src="https://github.com/thdwjdrl401/locus/raw/main/docs/assets/locus-robots.gif" width="560" alt="Locus 실시간 모니터링 화면">

- 4코어 서버에서 위치 데이터 **초당 10,000건**을 63분간 유실 없이 저장 (개선 전 초당 33건)
- 볼 곳
  - [부하 테스트 결과](https://github.com/thdwjdrl401/locus/blob/main/docs/PERFORMANCE.md): 단계별 병목, 변경 전후 처리량
  - [측정 기록 11편](https://github.com/thdwjdrl401/locus/tree/main/docs/measurements): 단건 INSERT부터 60분 통합 테스트까지
  - [설계 결정 기록(ADR) 8편](https://github.com/thdwjdrl401/locus/tree/main/docs/decisions): 선택한 방식과 기각한 대안

### [dev_retrospective](https://github.com/thdwjdrl401/dev_retrospective) · 실무 기술 회고

회사 코드는 공개할 수 없어, 담당했던 개발·운영 작업을 문제, 원인, 조치, 결과 순서로 정리했습니다.

- [모이소](https://github.com/thdwjdrl401/dev_retrospective/tree/main/moiso) (경상북도 모바일 도민증): N+1 해결로 관리자 조회 **10초 이상 → 0.5초 이내**, 취약점 진단 8개 항목 조치
- [카썹](https://github.com/thdwjdrl401/dev_retrospective/tree/main/carsub), [덕성여대 산학협력단](https://github.com/thdwjdrl401/dev_retrospective/tree/main/duksung_rnd), [tomas](https://github.com/thdwjdrl401/dev_retrospective/tree/main/tomas), [사내 운영 대시보드](https://github.com/thdwjdrl401/dev_retrospective/tree/main/asnet_dashboard)

### [기술 노트](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi) · 내부 코드를 따라간 기록

- [Spring Boot는 어떤 ApplicationContext를 사용할까](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/Spring%20Boot%EB%8A%94%20%EC%96%B4%EB%96%A4%20ApplicationContext%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%A0%EA%B9%8C.md): AOT, Native Image 직접 빌드 비교
- 브라우저의 요청은 스프링에 오기 전에 어디를 지날까 [1편](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/%5BJAVA%5D-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98%20%EC%9A%94%EC%B2%AD%EC%9D%B4%20%EC%8A%A4%ED%94%84%EB%A7%81%EA%B9%8C%EC%A7%80%20%EC%98%A4%EA%B8%B0%EA%B9%8C%EC%A7%80.md) · [2편](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/%5BJAVA%5D-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98%20%EC%9A%94%EC%B2%AD%EC%9D%B4%20%EC%8A%A4%ED%94%84%EB%A7%81%EA%B9%8C%EC%A7%80%20%EC%98%A4%EA%B8%B0%EA%B9%8C%EC%A7%802.md): Tomcat 11 소스 코드로 요청 처리 흐름 추적

---

### 코드 비공개 프로젝트

- **집현전** (SSAFY 6인, 우수상): 실시간 라이브 강의 플랫폼. WebRTC SFU 자체 호스팅, 실시간 자막(Redis Streams, WebSocket), 웹 푸시 알림 담당
- **100만 명 웹 푸시 발송** (집현전 확장, 개인): 발송 시간 **61시간 21분 → 5분 48초**. Transactional Outbox, RabbitMQ, HTTP/2 동시 발송. [개선 과정 문서](https://portfolio.thdwjdrl.com/notification/)

### 연락

- thdwjdrl401@gmail.com

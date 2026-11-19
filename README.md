# 송정기 · 백엔드 개발자

- **경력**: (주)에즈넷 개발팀 1년 7개월 (2024.03 ~ 2025.09), 경상북도 공공 마이데이터 플랫폼(사용자 약 20만 명) API 서버·관리자 웹·Flutter 앱 개발·운영
- **현재**: SSAFY 15기 Java 트랙, 대량 데이터 처리 개인 프로젝트

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![TimescaleDB](https://img.shields.io/badge/TimescaleDB-FDB515?style=flat-square&logo=timescale&logoColor=black) ![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white) ![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=flat-square&logo=rabbitmq&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

## 실무

### 모이소 · 경상북도 공공 마이데이터 플랫폼

| 문제 | 조치 | 결과 |
|---|---|---|
| 근무상황표 조회 N+1 | 일괄 조회, 3단계 Map 인덱싱, 2단계 페이징 | **10초 이상 → 0.5초 이내** |
| 외부 보안 진단 지적 사항 (대표: 주민등록번호 평문 메모리 잔존) | Frida 메모리 덤프로 재현 후 입력부터 전송까지 처리 구조 변경 | **취약점 8개 항목 조치**, 이행진단 통과 |
| 첨부파일 암호화 전환 | 4바이트 매직 넘버로 포맷 판별, Base64·AES/CBC 동시 지원 | **서비스 중단 없이 전환** |

코드 비공개 · [실무 기술 회고](https://github.com/thdwjdrl401/dev_retrospective)

---

## 개인 프로젝트

### 100만 명 웹 푸시 발송 · 61시간 21분 → 5분 48초

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/push-architecture-dark.png">
  <img src="assets/push-architecture.png" width="100%" alt="강의 자료 게시 → Outbox → RabbitMQ 팬아웃 큐 → 팬아웃 워커 N개 → notification 테이블과 Outbox → 웹 푸시 큐 → 푸시 워커 N개">
</picture>

측정 환경: 노트북 1대(물리 4코어), FCM Mock 서버(왕복 230ms)

| 병목 지표 | 조치 | 결과 |
|---|---|---|
| 게시 API 220.9초 (수신자 1,000명, 동기 처리) | Transactional Outbox, RabbitMQ 팬아웃 | **게시 응답 0.42초** |
| PostgreSQL OOM (수신자 100만 명 일괄 조회) | 커서 기반 분할 조회 | **OOM 해소** |
| 앱 CPU 376% / 한도 400% | 암호 객체 ThreadLocal 재사용 | **건당 5.95ms → 0.36ms** |
| 순차 발송 4.2건/s (왕복 230ms) | HTTP/2 멀티플렉싱 동시 발송 | **3,283건/s** |

웹 푸시 1,097,488건 전부 성공 (유실·429·5xx 0건) · 코드 비공개 · [개선 과정 문서](https://portfolio.thdwjdrl.com/notification/)

### [Locus](https://github.com/thdwjdrl401/locus) · 위치 데이터 적재 초당 33건 → 10,000건

측정 환경: 4코어 8GB 5400rpm HDD 단일 서버, k6

| 병목 지표 | 조치 | 결과 |
|---|---|---|
| CPU 2~8%, 디스크 %util 97% (커밋마다 fsync) | 인메모리 큐 + 배치 INSERT, TimescaleDB 전환 | **33 → 5,459 rows/s** |
| 단일 배치 워커, 디스크 사용률 59%에서 정체 | 워커 16개 병렬화, TreeMap 락 순서로 데드락 제거, 청크 주기 5분 | **초당 10,000건 63분 유실 0건** |

[코드](https://github.com/thdwjdrl401/locus) · [부하 테스트 결과](https://github.com/thdwjdrl401/locus/blob/main/docs/PERFORMANCE.md) · [설계 결정 기록](https://github.com/thdwjdrl401/locus/tree/main/docs/decisions)

### 집현전 · 실시간 라이브 강의 플랫폼 (SSAFY 6인, 우수상)

- Backend & Infra: WebRTC SFU(LiveKit) 자체 호스팅, 웹 푸시 알림
- 실시간 자막: Redis Streams 별도 Consumer Group, eventId 멱등 저장, 커밋 후 WebSocket 전달

코드 비공개

---

## 기술 노트

- [Spring Boot는 어떤 ApplicationContext를 사용할까](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/Spring%20Boot%EB%8A%94%20%EC%96%B4%EB%96%A4%20ApplicationContext%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%A0%EA%B9%8C.md): AOT, Native Image 직접 빌드 비교
- [브라우저의 요청은 스프링에 오기 전에 어디를 지날까](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/%5BJAVA%5D-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98%20%EC%9A%94%EC%B2%AD%EC%9D%B4%20%EC%8A%A4%ED%94%84%EB%A7%81%EA%B9%8C%EC%A7%80%20%EC%98%A4%EA%B8%B0%EA%B9%8C%EC%A7%80.md): Tomcat 11 소스 코드로 요청 처리 흐름 추적

## 연락

- thdwjdrl401@gmail.com

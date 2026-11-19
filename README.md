# 송정기

**지표로 병목을 확인하고 구조를 바꾸는 백엔드 개발자**

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white) ![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=flat-square&logo=rabbitmq&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

---

### 지표로 병목을 확인하고 개선합니다

<table>
<tr>
<td width="50%" align="center">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/push-architecture-dark.png">
  <img src="assets/push-architecture.png" alt="강의 자료 게시 → Outbox → RabbitMQ 팬아웃 큐 → 팬아웃 워커 N개 → notification 테이블과 Outbox → 웹 푸시 큐 → 푸시 워커 N개">
</picture>
</td>
<td width="50%" align="center"><img src="https://github.com/thdwjdrl401/locus/raw/main/docs/assets/locus-robots.gif" alt="Locus 실시간 모니터링 화면"></td>
</tr>
<tr>
<td align="center">100만 명 웹 푸시 발송 구조</td>
<td align="center">Locus 실시간 모니터링</td>
</tr>
</table>

- **웹 푸시 100만 건 발송: 61시간 21분 → 5분 48초**
  - Transactional Outbox, RabbitMQ, HTTP/2 동시 발송 · [개선 과정 문서](https://portfolio.thdwjdrl.com/notification/)
- **위치 데이터 저장: 초당 33건 → 초당 10,000건** (4코어 서버, 63분 유실 없음)
  - 배치 INSERT, TimescaleDB, 저장 워커 병렬화 · [코드](https://github.com/thdwjdrl401/locus) · [부하 테스트 결과](https://github.com/thdwjdrl401/locus/blob/main/docs/PERFORMANCE.md)

### 운영 중인 서비스를 안전하게 바꿉니다

공공 모바일 서비스(사용자 약 20만 명) 백엔드 개발·운영 1년 7개월

- **관리자 조회: 10초 이상 → 0.5초 이내** (N+1 쿼리 해결)
- **보안 취약점 8개 항목 조치** (외부 진단 후 재진단 통과)
- **첨부파일 암호화 무중단 전환** (Base64와 AES/CBC 동시 지원)
- [실무 기술 회고](https://github.com/thdwjdrl401/dev_retrospective)

### 내부 동작을 소스 코드로 확인합니다

- **Spring Boot ApplicationContext**: AOT, Native Image 직접 빌드 비교 · [글](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/Spring%20Boot%EB%8A%94%20%EC%96%B4%EB%96%A4%20ApplicationContext%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%A0%EA%B9%8C.md)
- **Tomcat 11 요청 처리 흐름**: Coyote부터 DispatcherServlet까지 · [1편](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/%5BJAVA%5D-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98%20%EC%9A%94%EC%B2%AD%EC%9D%B4%20%EC%8A%A4%ED%94%84%EB%A7%81%EA%B9%8C%EC%A7%80%20%EC%98%A4%EA%B8%B0%EA%B9%8C%EC%A7%80.md) · [2편](https://github.com/SSAFY-CS-STUDY-15th/SongJeongKi/blob/java/from-browser-to-spring-process/%5BJAVA%5D-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98%20%EC%9A%94%EC%B2%AD%EC%9D%B4%20%EC%8A%A4%ED%94%84%EB%A7%81%EA%B9%8C%EC%A7%80%20%EC%98%A4%EA%B8%B0%EA%B9%8C%EC%A7%802.md)

---

### 프로젝트

- **[집현전]** 실시간 라이브 강의 플랫폼 (SSAFY 6인, 우수상): WebRTC SFU 자체 호스팅, 실시간 자막, 웹 푸시 알림
- **[집현전 확장]** 100만 명 웹 푸시 발송 시스템 (개인)
- **[[Locus](https://github.com/thdwjdrl401/locus)]** 디바이스 위치·상태 데이터 수집 및 모니터링 서버 (개인)
- **[모이소]** 경상북도 모바일 도민증 ((주)에즈넷)

### 연락

- thdwjdrl401@gmail.com

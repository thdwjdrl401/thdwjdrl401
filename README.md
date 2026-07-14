# Song JeongKi
## Backend Developer

Java/Spring 기반 백엔드 개발자입니다. 공공 서비스를 기획부터 개발·배포·운영까지 단독으로 책임지며, 성능 저하·보안 취약점·WAF 장애·외부 API 연동을 로그와 데이터 흐름을 따라 원인부터 분석하고 개선해 왔습니다.
익숙한 원인으로 단정하지 않고 실제 원인을 확인한 뒤 구조를 바로잡습니다 — 이 방식을 공개 코드로 보여주는 개인 프로젝트가 아래 **Locus**입니다.

---

## Locus — 측정 주도 실시간 텔레메트리 파이프라인

**[github.com/thdwjdrl401/locus](https://github.com/thdwjdrl401/locus)**  ·  Java · Spring Boot · TimescaleDB · Redis Streams · MQTT

물리 디바이스(폰·로봇 등)가 위치·상태를 실시간으로 올리고 한 명이 다수를 모니터링하는 백본. 추측이 아니라 부하 측정으로 병목을 규명하고 개선합니다.

- **단일 노후 박스(4코어·8GB·5400rpm HDD)에서 1만 대 × 1Hz를 전 구간(HTTP → Redis Streams → TimescaleDB) 60분+ 유실 없이 처리** — 발신 ≈ 수신 ≈ 저장을 양끝 정산으로 확인.
- 적재 33 → 지속 10k rows/s: 병목(커밋당 fsync → 랜덤 쓰기 → 단일 배치 워커)을 단계마다 재현·귀속하고 before/after로 개선. 인입 최대 처리량의 병목이 스토리지가 아니라 박스 CPU임을 코어 핀 6→8 선형 확장(12K→16K)으로 규명.
- 관제 조회 p95 8.65s → 35ms: 디바이스별 최신 조회의 상관 서브쿼리를 `LATERAL`로 재설계.
- 디바이스 추상화(PHONE·AMR): 새 타입을 더해도 판정 엔진·엔티티는 불변, 경계는 ArchUnit이 빌드 단에서 강제. AMR 상태 스키마는 개방 표준(ROS 2·VDA5050) 참조로 독립 정의.
- **지오펜스 판정 엔진(`core.engine`, 미션·타입 무지) — 진행 중(M5).** 로봇이 작업구역 경계를 넘나들면 ENTER/EXIT를 판정해 관제 화면에 이벤트로(아래 데모).

<p align="center">
  <img src="https://github.com/thdwjdrl401/locus/raw/main/docs/assets/locus-robots.gif" width="70%" alt="Locus 실시간 관제 — 로봇 지오펜스 판정"/>
</p>

각 단계의 before → 변경 → after → 해석은 측정 문서로, 결정과 기각한 대안은 [ADR](https://github.com/thdwjdrl401/locus/tree/main/docs/decisions)·[리스크 등록부](https://github.com/thdwjdrl401/locus/blob/main/docs/RISKS.md)로 공개합니다.

---

## 운영 경험

> 회사 프로젝트는 코드가 비공개라 git 히스토리·실제 작업 기반 기술 회고로 대신합니다 → **[DevRetrospective](https://github.com/thdwjdrl401/dev_retrospective)**

약 20만 사용자 공공 플랫폼의 한 서비스를 화면 기획부터 배포·운영·감리 대응까지 단독으로 책임졌습니다.

- **조회 구조 재설계** — 관리자 조회가 한 달치에서 10초 이상. 전부 가져와 후처리하던 구조가 원인임을 확인하고, 목록 단위 페이징 후 상세만 재조회하는 2단계로 재설계해 0.5초 이내로 단축.
- **메모리 평문 잔류 취약점** — 단말 메모리에 주민번호가 평문으로 남는 문제를, Dart String 불변성이 원인임을 확인하고 가변 버퍼 + 즉시 암호화 구조로 재설계.
- **WAF 장애 분석** — 이미지 업로드가 200 응답에도 실패하던 문제의 원인을 추적하고 정책 조정을 지원.
- **외부 API 배치 동기화** — 보조금24/공공 API 연동, 변경분 중심의 데이터 동기화.
- **JPA 더티 체킹 이슈** — 의도치 않은 UPDATE를 쿼리 로그로 추적해 원인 규명.

---

## Tech Stack

### Main
![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C?style=for-the-badge)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

### Data & Infra
![TimescaleDB](https://img.shields.io/badge/TimescaleDB-FDB515?style=for-the-badge&logo=timescale&logoColor=black)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

### Used
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![MQTT](https://img.shields.io/badge/MQTT-660066?style=for-the-badge&logo=mqtt&logoColor=white)
![k6](https://img.shields.io/badge/k6-7D64FF?style=for-the-badge&logo=k6&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![MyBatis](https://img.shields.io/badge/MyBatis-000000?style=for-the-badge)

---

## Repositories

| Repo | 설명 |
|---|---|
| **[Locus](https://github.com/thdwjdrl401/locus)** | 실시간 디바이스 텔레메트리 파이프라인 — 측정 주도(부하로 병목 규명·개선), Spring Boot·TimescaleDB·Redis Streams·MQTT. 단독 |
| **[DevRetrospective](https://github.com/thdwjdrl401/dev_retrospective)** | 회사 프로젝트 기술 회고 (모이소·덕성여대·토마스·카썹) — 코드 비공개, 기여 정리 |
| **[LingoLens](https://github.com/thdwjdrl401/LingoLens)** | 다국어 웹페이지 번역 Chrome 확장 (TypeScript, MV3) — 단독 개발 |
<!--| **[TripCraft](https://github.com/thdwjdrl401/TripCraft)** | 이동 시간 기반 여행 일정 플래너 (Spring Boot, 멀티 API 통합) — 팀 | -->

---

## Problem Solving

BOJ로 자료구조와 알고리즘을 학습하고 있습니다. 정답 코드뿐 아니라 접근 방식, 실패 원인, 시간·공간복잡도를 함께 정리하는 것을 목표로 합니다.

[![Solved.ac Profile](http://mazassumnida.wtf/api/v2/generate_badge?boj=thdwjdrl401)](https://solved.ac/thdwjdrl401/)

# Song JeongKi
## Backend Developer

Java/Spring 기반 백엔드 개발자입니다.
공공 서비스를 기획부터 개발·배포·운영까지 단독으로 책임지며, 운영 중 발생한 성능 저하, 보안 취약점, 외부 API 연동, WAF 장애를 로그와 데이터 흐름을 따라 원인부터 분석하고 개선해 왔습니다.
문제가 생겼을 때 익숙한 원인으로 단정하지 않고, 실제 원인이 어디에 있는지 확인한 뒤 구조를 바로잡는 방식으로 일합니다.

---

## What I Focus On

- **단독 오너십** — 약 20만 사용자 공공 플랫폼의 한 서비스를 화면 기획부터 배포·운영·감리 대응까지 혼자 책임진 경험
- **원인부터 보는 문제 해결** — 증상에 임시 조치를 더하기보다, 로그·데이터·공식 문서로 실제 원인을 확인하고 구조적으로 해결
- **운영 안정성** — 성능 저하·장애·보안 취약점을 운영 중에 진단하고, 재발하지 않도록 개선

---

## Selected Work

> 회사 프로젝트는 코드가 비공개라, git 히스토리와 실제 작업 기반으로 정리한 기술 회고로 대신합니다 → **[Portfolio](https://github.com/thdwjdrl401/dev-retrospective)**

- **조회 구조 재설계** — 관리자 조회 화면이 한 달 조회 시 10초 이상 → 전부 가져와 후처리하던 구조가 원인임을 확인하고, 목록 단위 페이징 후 상세만 재조회하는 2단계 구조로 재설계해 0.5초 이내로 단축
- **메모리 평문 잔류 취약점 개선** — 단말 메모리에 주민번호가 평문으로 남는 문제를, Dart String 불변성이 원인임을 확인하고 가변 버퍼 + 즉시 암호화 구조로 재설계
- **WAF 장애 분석** — 이미지 업로드가 200 응답에도 실패하던 문제의 원인을 추적하고 정책 조정을 지원
- **외부 API 배치 동기화** — 보조금24/공공 API 연동, 변경분 중심의 데이터 동기화
- **JPA 더티 체킹 이슈 해결** — 의도치 않은 UPDATE를 쿼리 로그로 추적해 원인 규명

---

## Tech Stack

### Main
![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C?style=for-the-badge)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

### Infra & Operation
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

### Used
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![MyBatis](https://img.shields.io/badge/MyBatis-000000?style=for-the-badge)

---

## Repositories

| Repo | 설명 |
|---|---|
| **[portfolio](https://github.com/thdwjdrl401/dev-retrospective)** | 회사 프로젝트 기술 회고 (모이소·덕성여대·토마스·카썹) — 코드 비공개, 기여 정리 |
| **[LingoLens](https://github.com/thdwjdrl401/LingoLens)** | 다국어 웹페이지 번역 Chrome 확장 (TypeScript, MV3) — 단독 개발 |
| **[TripCraft](https://github.com/thdwjdrl401/TripCraft)** | 이동 시간 기반 여행 일정 플래너 (Spring Boot, 멀티 API 통합) — 팀 |

---

## Problem Solving

BOJ로 자료구조와 알고리즘을 학습하고 있습니다. 정답 코드뿐 아니라 접근 방식, 실패 원인, 시간·공간복잡도를 함께 정리하는 것을 목표로 합니다.

[![Solved.ac Profile](http://mazassumnida.wtf/api/v2/generate_badge?boj=thdwjdrl401)](https://solved.ac/thdwjdrl401/)

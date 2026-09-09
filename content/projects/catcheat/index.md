---
title: "CatchEat"
date: 2026-06-30
summary: "예약·선착순 쿠폰·빈자리 알림·AI 챗봇을 포함한 레스토랑 예약 플랫폼 백엔드 고도화 프로젝트"
tags:
  - Backend
  - Performance
  - Spring Boot
tech_stack:
  - Spring Boot
  - PostgreSQL
  - PostGIS
  - Redis
  - Redisson
  - Kafka
  - Resilience4j
  - Prometheus
  - Grafana
  - Loki
  - JWT/OAuth2
links:
  - type: github
    url: https://github.com/catchtable-clone/backend
    label: Backend
  - type: github
    url: https://github.com/catchtable-clone/frontend
    label: Frontend
featured: true
status: "완료"
role: "팀원 (백엔드)"
duration: "2026.04 ~ 2026.06"
team_size:
highlights:
  - "위치 기반 검색 P95 12,587ms → 245ms (51배)"
  - "매장 118,725건 기준 반경 검색 인덱스 전환"
  - "Resilience4j 서킷브레이커로 외부 API 장애 격리"
  - "k6 부하 테스트 파이프라인 직접 구축"
---

캐치테이블을 참고해 만든 레스토랑 예약 플랫폼입니다. 기능 구현보다는 **실제 요청 흐름에서 발생하는 병목과 장애 전파를 찾아 개선하는 것**에 초점을 둔 백엔드 고도화 프로젝트였습니다.

> **TODO** — 프로젝트 배경(왜 이 주제를 골랐는지), 팀 구성과 본인 담당 범위, 전체 기능 목록을 여기에 추가하세요.

## 개요

| | |
|---|---|
| 기간 | 2026.04 ~ 2026.06 |
| 역할 | 팀원 (백엔드) |
| 기술 스택 | Spring Boot, PostgreSQL(PostGIS), Redis(Redisson), Kafka, Resilience4j, Prometheus/Grafana/Loki, JWT/OAuth2 |
| 저장소 | [catchtable-clone/backend](https://github.com/catchtable-clone/backend) · [frontend](https://github.com/catchtable-clone/frontend) |

## 아키텍처

> **TODO** — 시스템 구성도를 넣으세요. 이미지는 이 폴더에 두고 `![구성도](architecture.png)`로 참조하거나, 코드 블록에 ASCII 다이어그램을 넣으면 됩니다.

---

## 1. 위치 기반 매장 검색 성능 개선

### 문제

매장 **118,725건** 기준 반경 검색에서 전체 데이터를 순차 스캔하는 구조였고, k6 측정 결과 **P95 12,587ms**가 나왔습니다.

> **TODO** — 기존 쿼리와 실행 계획(`EXPLAIN ANALYZE`) 결과를 붙여 두면 병목이 어디였는지가 명확해집니다.

### 원인 분석

거리 계산이 모든 행에 대해 수행된 뒤 정렬되는 구조여서, 반경 필터링이 인덱스 단계에서 전혀 걸러지지 않았습니다.

> **TODO** — 어떤 방법으로 이 결론에 도달했는지(실행 계획 확인, 로그 분석 등) 과정을 적어 주세요.

### 해결

공간 데이터 전용 인덱스인 **PostGIS GIST**를 도입해, 범위 필터링과 거리 정렬을 인덱스 단계에서 처리하도록 전환했습니다.

> **TODO** — 개선 후 쿼리, 인덱스 DDL, 검토했지만 선택하지 않은 대안(예: 지오해시, 격자 분할)과 그 이유를 적으면 좋습니다.

### 결과

| 지표 | 개선 전 | 개선 후 |
|---|---|---|
| P95 응답시간 | 12,587ms | **245ms** |

약 **51배** 개선했습니다.

---

## 2. 서킷브레이커 기반 외부 API 장애 격리

### 문제

결제 등 외부 API에 장애가 발생하면 연쇄 실패로 전체 서비스 응답이 지연될 가능성을 확인했습니다.

### 해결

**Resilience4j 서킷브레이커**를 적용해 장애 전파를 차단하고, 빠른 Fallback 처리를 구현했습니다.

> **TODO** — 서킷브레이커 설정값(failureRateThreshold, waitDurationInOpenState 등)을 어떤 근거로 정했는지, Fallback이 실제로 어떤 응답을 반환하는지 적어 주세요. 장애 주입 테스트 결과가 있다면 함께 넣으면 설득력이 큽니다.

---

## 3. k6 부하 테스트 환경 구축

성능 개선 전후를 정량적으로 비교하기 위해 **k6 부하 테스트 파이프라인을 직접 구축**했습니다. P95/TPS 지표를 기준으로 병목을 식별하고 개선 효과를 측정하는 데 활용했습니다.

> **TODO** — 테스트 시나리오(가상 유저 수, ramp-up, 지속 시간)와 실행 환경(로컬/도커/CI), 그리고 k6 스크립트 일부를 넣어 주세요.

---

## 그 외 구현

> **TODO** — 이력서에 넣지 못한 작업들을 여기에 정리하세요.
>
> - 선착순 쿠폰: Redisson 분산 락 / 재고 차감 동시성 처리
> - 빈자리 알림: Kafka 기반 이벤트 발행·구독
> - AI 챗봇
> - 인증: JWT / OAuth2
> - 모니터링: Prometheus / Grafana / Loki 구성

## 배운 점

> **TODO** — 이 프로젝트에서 얻은 결론을 적어 주세요. "무엇을 했다"보다 "왜 그렇게 판단했고 다음엔 어떻게 하겠다"가 읽는 사람에게 남습니다.

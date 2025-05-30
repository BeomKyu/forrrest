# Forrrest 프로젝트 요약 및 로드맵

## 1. 전체 아키텍처

* **마이크로서비스 구성**: AuthService, UserService, AppManagementService, Gateway, FriendService, ChatService, CalendarService, DriveService, MailService
* **API Gateway**: Spring Cloud Gateway 기반 라우팅, JWT 인증 필터, 로깅·모니터링 PoC
* **실시간 메시징**: WebSocket + Redis Pub/Sub를 통한 메시지 브로드캐스트
* **데이터 저장소**: 서비스별 MySQL (메시지 저장용 테이블 포함)
* **CI/CD 파이프라인**: 로컬 Docker Compose, 프로덕션 Kubernetes 배포, GitHub Actions 자동화

## 2. 현재 구현된 기능

* **common 모듈**: JWT 생성·검증, Spring Security 필터 통합
* **auth-service**: 회원가입, 로그인, Access/Refresh 토큰 발급·갱신, 프로필 CRUD
* **app-management-service**: 앱 등록 및 앱 관리, Nonce 토큰 발급·인증
* **gateway**: 라우팅 PoC, JWT 인증 필터 적용

## 3. 향후 구현 예정 기능

### 3.1 MVP (최소 기능 제품)

1. **gateway**: 라우팅 PoC, JWT 인증 필터 적용
2. **API Gateway 강화**: CORS, Rate Limiting, TLS 지원
3. **FriendService**: 친구 요청·수락·삭제, 목록 조회, 차단 기능
4. **ChatService**: 실시간 채팅, 메시지 영속화, 읽음 처리
5. **UserService**: 프로필 및 보안 관리, 활동 로그 기록

### 3.2 추가 확장 기능

* **CalendarService & DriveService**: 일정 관리, 파일 저장·조회
* **MailService**: 이메일 송수신, 스팸 필터링
* **로깅·모니터링**: ELK 스택, Prometheus 연동
* **알림 서비스**: NotificationService 이벤트 발행
* **소셜 로그인 & MFA**: Google/GitHub OAuth2, 2단계 인증(TOTP)
* **Secret/Key Rotation & 블랙리스트 관리**: 주기적 키 교체, 토큰 무효화

## 4. 프로젝트 개요

Forrrest는 올인원 협업 플랫폼 백엔드를 목표로, 공통 인증·인가 모듈과 독립 실행형 마이크로서비스 아키텍처를 통해 확장성과 유지보수성을 확보합니다.

## 5. 목표

* **장기 목표**: 단일 인증 체계로 모든 협업 도구 통합
* **단기 목표 (MVP)**: 인증, 사용자·앱 관리, Gateway, 친구·채팅·일정·메일 핵심 기능 구현

## 6. 핵심 기능 및 우선순위

|  단계 | 기능                                         |  상태 |
| :-: | ------------------------------------------ | :-: |
| 1단계 | 인증·인가 및 프로필 CRUD                           |  완료 |
| 2단계 | 앱 관리                         |  완료 |
| 3단계 | Gateway PoC                         |  예정 |
| 4단계 | FriendService, ChatService 구현 |  예정 |
| 5단계 | ChatService 구현 |  예정 |

## 7. 로드맵 & 일정

|    주차   | 마일스톤                                |
| :-----: | ----------------------------------- |
|   1주차   | 공통 모듈 안정화, DB 스키마 확정                |
|   2주차   | AuthService·UserService 기능 완성 및 테스트 |
|   3주차   | AppManagementService 완성, Gateway 배포 |
|   4주차   | FriendService 설계 및 Skeleton 개발      |
|  5\~6주차 | ChatService Skeleton 개발 및 통합 테스트 및 배포       |

## 8. 성공 지표 (KPI)

* **인증 API 응답 시간 (P95)**: ≤ 200ms
* **월간 활성 사용자(MAU) 목표**: 달성 여부
* **빌드 성공률**: ≥ 95%
* **채팅 지연 시간 (P95)**: ≤ 100ms
* **친구·알림 활성화율**: ≥ 80%


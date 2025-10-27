# 소중한 오픈소스 활용 SW 경진대회
## 국립한밭대학교 kimbanana(김바나나) 팀

## 주제
- 실시간 협업 캔버스 히스토리 및 복원 시스템

## 팀 구성
- 20221023 신보연 모바일융합공학과
- 20221038 임예은 모바일융합공학과
- 20221037 이혜현 모바일융합공학과

## Project Background

### 개요
실시간 협업 캔버스 히스토리 및 복원 시스템은
웹 기반 환경에서 다중 사용자가 프레젠테이션을 동시에 작성·편집할 수 있도록 지원하는 실시간 협업 도구입니다.

- STOMP 기반 WebSocket 구조를 활용해 사용자 간 실시간 동기화 환경 제공
- CRDT 알고리즘(Yjs) 도입으로 충돌 없는 병합 처리
- 슬라이드 단위 히스토리 기록 및 선택적 복원 기능 구현

### 필요성
1. 동기화 충돌 문제 해결
   - 동시 편집 환경에서 발생하는 충돌을 CRDT 기반 자동 병합으로 해결

2. 세분화된 히스토리 복원 기능
   - 전체 문서가 아닌 특정 슬라이드 단위 복원 기능 제공

3. 서비스 수준 기술 도입 및 학습
   - JWT 인증, OAuth2, 파일 만료 스케줄링, Swagger 문서화 등 실무 기반 기술 학습 및 설계 경험

4. 교육·협업 환경에서의 실질적 필요성
   - 온라인 수업/팀 프로젝트 등 다중 사용자가 동시에 프레젠테이션을 제작하는 상황에 적합

## 프로젝트 내용

### 구현 내용
- 실시간 동시 편집 기능
  - 슬라이드 단위 구독 구조 설계 (WebSocket + STOMP)
  - 사용자 간 편집 이벤트 실시간 송수신
  - CRDT(Yjs) 기반 병합 처리로 충돌 방지

- 히스토리 기록 및 복원 기능
  - 슬라이드별 변경 이력 DB 저장
  - 특정 시점의 슬라이드만 복원 가능한 API 제공

- JWT 기반 인증 및 권한 관리
  - 토큰 기반 REST API 인증
  - WebSocket 연결 시 인증 검증
  - Google OAuth2 연동

- 파일 업로드 및 자동 만료 기능
  - 이미지 업로드 후 접근 URL 반환
  - 일정 시간 후 자동 삭제 (스케줄링 기반)

- Swagger 기반 API 문서 자동화
  - OpenAPI 스펙 기반 자동 명세 생성

### 시스템 아키텍처

<img width="1000" height="560" alt="image" src="https://github.com/user-attachments/assets/55d044fd-9104-4a78-aeeb-d04eee4d721e" />

### UI/UX

<table>
  <tr>
    <td><img width="600" src="https://github.com/user-attachments/assets/a5b6d752-c632-40fe-a1f4-723525dfd609" /></td>
    <td><img width="600" src="https://github.com/user-attachments/assets/64a00d05-3f08-44bc-a8e8-2a8db2958af7" /></td>
  </tr>
  <tr>
    <td><img width="600" src="https://github.com/user-attachments/assets/aee168cb-c204-43e3-a6f9-d1782b911822" /></td>
    <td><img width="600" src="https://github.com/user-attachments/assets/28bb92c4-0a02-4faf-93e1-63952b323305" /></td>
  </tr>
</table>

</br>

### 기대 효과
- 실시간 협업 충돌 방지 및 안정성 확보
  - CRDT를 통한 실시간 동시 편집 충돌 자동 병합
  - 성능 저하 없이 효율적인 사용자 간 협업 가능

- 정밀한 히스토리 복원 및 관리 기능
  - 슬라이드 단위의 시점 복원 기능으로 실수 복구 용이
  - 전체 되돌리기 방식보다 높은 유연성 제공

- 자동화된 히스토리 버전 관리 시스템 제공
  - 변경 이력 자동 저장 및 삭제
  - 설정된 기준에 따라 주기적으로 정리
  - 안정적이고 일관된 히스토리 관리 가능

- 확장성과 유지보수성이 높은 구조 설계
  - WebSocket + REST API 이중 구조 설계
  - OAuth2 기반 인증 연동 확장성 확보

- 기술적 확장성 확보
  - 실시간 동기화, 충돌 해결, 슬라이드 단위 히스토리 복원 등은
    문서 편집기, 협업 디자인 도구 등 다양한 시스템으로의 확장 가능
  - 이벤트 기반 아키텍처 및 STOMP 구조는 재사용성 높음

- 교육, 발표, 협업 도구로의 응용 가능성
  - 온라인 강의, 프로젝트 발표 등 협업 환경에 쉽게 접목 가능
  - 향후 화상회의, 메타버스 등 시스템과의 통합 가능

## 개발환경
- DBMS: PostgreSQL
- 백엔드 개발 언어: Java (Spring Boot)
- 프론트엔드 개발 언어: TypeScript (React + Konva.js)
- 실시간 통신: WebSocket (STOMP Protocol)
- 충돌 해결 알고리즘: CRDT (Yjs)
- 인증 및 보안: JWT (Access Token), OAuth2
- 빌드 및 배포: Gradle, GitHub Actions, Docker
- 협업 도구: GitHub (버전 관리), Notion (기획), Figma (UI/UX)
- 테스트 및 문서화: JUnit, Swagger (OpenAPI 자동 문서화)

![header](https://capsule-render.vercel.app/api?type=blur&color=C2EEFD&height=300&section=header&text=MallangOrder&fontSize=90)


##  프로젝트 소개

- '말랑오더'는 AI를 활용한 음성 인식 주문을 지원하여 디지털 소외 계층도 쉽게 이용할 수 있도록 구현된 배리어 프리(Barrier-Free) 키오스크 시스템입니다.
- 시연 영상(클릭하여 재생⬇️)

  https://youtu.be/xeWMnRbKrRQ

<p align="center">
  <img src="images/key_features_and_ui_overview.png" alt="주요 기능 및 UI 개요" width="800"/>
</p>

<p align="center">
  <img src="images/system_architecture.png" alt="시스템 구조도" width="800"/>
</p>


## 프로젝트 목표
- 음성 + 화면 안내 및 AI 기반 맥락 인식을 통해 사용자 접근성 혁신.

- 웹앱 기반 시스템으로 저비용 도입을 가능하게 하며, 매장 운영 효율성 강화.


## 주요 기능

### 🗣️ AI 기반 맥락 인식 주문 시스템

- 대화 흐름 기반 응답: 키오스크별 최근 대화 내용(History)을 AI 서버로 전송하여 맥락을 인지하고 자연스러운 응답을 생성.

- 명확한 의도 분류: AI 서버의 응답을 받아 get_category, update_cart 등의 정해진 의도(Intent)로 분류하여 백엔드에서 해당 비즈니스 로직 실행.

- 다국어 지원: 음성 및 화면을 통한 다국어(한/영) 주문 처리 지원 로직 구현.

### 🛒 주문 및 결제 관리

- 메뉴/장바구니 관리: 메뉴 추천, 메뉴 탐색, 장바구니에 항목 추가/수정/삭제 API.

- 주문 관리: 주문 생성, 주문 상태 (대기, 처리 중, 완료) 업데이트 및 내역 확인 기능.

### 💼 관리자 시스템

- 가게 및 테이블 관리: 관리자 페이지를 통한 가게 정보 및 테이블 정보 등록/수정/삭제.

- 메뉴/카테고리 관리: 메뉴 및 카테고리 정보 CRUD 기능 및 AI 서버로 메뉴 정보 전송 로직.


## ERD
<p align="center">
  <img src="images/erd.png" alt="ERD" width="800"/>
</p>

## 기술 스택 (Tech Stacks)

### Back-End (핵심)
<div align="center">
  <img src="https://img.shields.io/badge/Java-21-007396?style=for-the-badge&logo=openjdk&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Boot-3.3.5-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white"/>
  <img src="https://img.shields.io/badge/QueryDSL-3475A9?style=for-the-badge&logoColor=white"/>
  <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black"/>
</div>

### Database / Cache
<div align="center">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white"/>
</div>

### Front-End
<div align="center">
  <img src="https://img.shields.io/badge/React-18.3.1-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white"/>
  <img src="https://img.shields.io/badge/Styled_Components-DB7093?style=for-the-badge&logo=styledcomponents&logoColor=white"/> 
  <img src="https://img.shields.io/badge/MUI-007FFF?style=for-the-badge&logo=mui&logoColor=white"/> 
  <img src="https://img.shields.io/badge/Day.js-3632d7?style=for-the-badge&logoColor=white"/>
</div>

### Tools (협업/참고)

<div align="center">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white"/>
</div>

## 백엔드 개발 상세 (담당)

### AI 서버 연동 및 대화 맥락 관리 (AI Integration & Context Management)

- API 통신 전담 모듈: AI 서버(Flask 기반)와의 통신을 위한 RESTful 클라이언트를 ai 도메인 내에 별도로 구현했습니다.

- 데이터 포맷 및 전송: 사용자 음성 텍스트 외에, AI가 주문 의도를 정확히 파악하도록 현재 키오스크별 메뉴 목록 및 **대화 히스토리(Context)**를 JSON 형태로 가공하여 AI 서버로 전송.

- 의도(Intent) 기반 주문 처리: AI 서버로부터 응답으로 받은 의도(e.g., update_cart, order, menu_search)를 분류하여, 백엔드 로직(주문/장바구니 서비스)으로 분기하여 실행함으로써 대화형 주문의 안정성을 확보.

- 시스템 구조 분리: AI 서버가 다운되더라도 핵심 DB와 인증 시스템에는 영향이 없도록 API 게이트웨이 역할을 분리하여 시스템 안정성을 강화.

### 인증 및 보안 시스템 구축

- JWT 기반 인증: Spring Security를 활용하여 관리자 및 사용자 인증을 JWT 토큰 기반으로 구현. Access Token과 Refresh Token을 분리하여 관리.

- Redis 활용 (토큰 관리): Refresh Token을 Redis에 저장하고 만료 시간을 관리하여 토큰의 안전한 재발급 및 세션 유지를 구현.

- HTTPS 적용: Let’s Encrypt를 통해 API 통신 구간에 HTTPS를 적용하여 데이터 보안 강화.

### 아키텍처 및 데이터 관리

- Gradle 환경 설정: 빌드 자동화 및 의존성 관리를 위해 Gradle을 메인 빌드 도구로 채택.

- 계층형 설계 및 JPA: Controller -> Service -> Repository의 표준 계층 분리를 통해 유지보수 용이성을 확보하고, JPA를 통해 객체 지향적인 데이터 접근 구현.

- MySQL & Redis 활용: MySQL은 메뉴/주문 등 영구 데이터를, Redis는 캐싱 및 관리자 세션 관리에 활용하여 성능과 신뢰성을 동시에 추구.

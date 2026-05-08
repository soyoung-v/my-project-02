# Airbnb Main Clone

Vue 3와 Vite를 기반으로 만든 Airbnb 메인 화면 클론 프로젝트입니다.

실제 Airbnb 서비스 기능을 재현한 프로젝트가 아니라, `public/airbnb.json`에 있는 로컬 목업 데이터를 활용해 메인 화면 UI를 구성한 프론트엔드 프로젝트입니다.

상단 탭 전환, 스크롤에 따른 sticky header 변화, 카드 캐러셀, 추천 여행지 라우팅, 푸터 링크 구성을 중심으로 화면을 구성했습니다.

## 기술 스택

- Vue 3
- Vite
- Vue Router
- Axios
- Swiper
- CSS

## 주요 기능

- 숙소 / 체험 / 서비스 탭 전환 UI
- 스크롤 시 sticky header 전환
- sticky 상태에서 축약형 검색 UI 표시
- 로컬 JSON 데이터 기반 카드 목록 렌더링
- Swiper 기반 카드 캐러셀
- 카드별 하트 아이콘 화면상 토글
- 추천 여행지 탭 라우팅
- 추천 여행지 더 보기 버튼
- 푸터 정보 링크 및 소셜 링크 구성

## 화면 구성

| 영역 | 설명 |
|---|---|
| Header | Airbnb 스타일의 상단 헤더, 숙소 / 체험 / 서비스 탭 전환, 스크롤 상태에 따른 검색 UI 변경 |
| Main | `public/airbnb.json` 데이터를 기반으로 카드 섹션 렌더링, 선택된 탭에 따른 데이터 필터링, Swiper 캐러셀 |
| Footer | 추천 여행지 탭 메뉴, 라우트에 따른 추천 여행지 목록 변경, 더 보기 버튼, 정보성 링크 및 소셜 링크 |

## 데이터 구조

메인 화면 데이터는 `public/airbnb.json` 파일을 사용합니다.

포함된 데이터는 다음과 같습니다.

- 카드 섹션 데이터
- 탭별 유형 정보
  - stay
  - experience
  - service
- 카드 이미지, 제목, 기간, 가격, 평점, 배지 정보
- 계속 검색하기 영역에 사용되는 일부 데이터

푸터 영역은 별도 정적 데이터 파일로 구성되어 있습니다.

```text
src/FooterData.js
src/airbnbinfodata.js
src/socialLinks.js
```

## 프로젝트 구조

```text
src/
├── components/
│   ├── header/
│   │   ├── HerderMom.vue
│   │   ├── TheHeader.vue
│   │   ├── SearchBar.vue
│   │   └── ContinueSearch.vue
│   ├── main/
│   │   ├── Airbnb.vue
│   │   └── LodgingItem.vue
│   └── footer/
│       ├── Destinations.vue
│       ├── AirbnbInfo.vue
│       └── LegalInfo.vue
├── router/
│   └── index.js
├── App.vue
├── main.js
├── FooterData.js
├── airbnbinfodata.js
└── socialLinks.js

public/
└── airbnb.json
```

## 주요 구현 포인트

### 탭 기반 화면 전환

숙소, 체험, 서비스 탭 상태에 따라 헤더 문구와 메인 카드 목록이 함께 변경됩니다.

### Sticky Header

`window.scrollY` 값을 기준으로 sticky header 상태를 제어합니다.  
스크롤 위치에 따라 기본 헤더와 축약형 검색 UI가 전환됩니다.

### 목업 데이터 기반 렌더링

`public/airbnb.json` 데이터를 불러와 메인 카드 목록을 구성합니다.  
선택된 탭 값에 따라 stay, experience, service 데이터를 필터링해 화면에 표시합니다.

### Swiper 카드 캐러셀

카드 섹션은 Swiper를 사용해 좌우 이동 가능한 캐러셀 UI로 구성했습니다.

### 추천 여행지 라우팅

Vue Router를 사용해 `/destinations/:category` 라우트를 구성했습니다.  
현재 경로를 기준으로 추천 여행지 목록을 변경합니다.

### 하트 아이콘 토글

카드 내부 하트 아이콘은 로컬 상태로만 토글됩니다.  
저장 기능이나 서버 연동은 포함되어 있지 않습니다.

## 실행 방법

### 1. 패키지 설치

```bash
npm install
```

### 2. 개발 서버 실행

```bash
npm run dev
```

브라우저에서 로컬 개발 서버 주소로 접속해 확인할 수 있습니다.

```text
http://localhost:5173
```

### 3. 빌드

```bash
npm run build
```

## 참고 사항

- 이 프로젝트는 실제 Airbnb 서비스 기능이 아닌 UI 중심 클론 프로젝트입니다.
- 데이터는 실제 API가 아니라 `public/airbnb.json` 기반 목업 데이터입니다.
- 검색창은 UI만 구성되어 있으며 실제 검색 기능은 없습니다.
- 하트 아이콘은 화면상 토글만 가능하며 저장되거나 유지되지 않습니다.
- 로그인, 회원가입, 예약, 결제, 백엔드 서버 기능은 포함되어 있지 않습니다.
- 일부 이미지와 영상은 외부 Airbnb CDN 리소스를 사용하므로 네트워크 상태에 따라 표시가 달라질 수 있습니다.

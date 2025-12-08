# S.Camp (스캠프)

> **AI 기반 사기 탐지 및 예방 플랫폼**  
> 실시간 사기 분석과 커뮤니티 기반 사례 공유로 더 안전한 디지털 환경을 만듭니다.

[![React](https://img.shields.io/badge/React-19.1.1-61dafb?logo=react)](https://reactjs.org/)
[![Vite](https://img.shields.io/badge/Vite-7.1.14-646cff?logo=vite)](https://vitejs.dev/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 🎯 프로젝트 소개

S.Camp는 **AI 기술**을 활용하여 피싱, 스미싱, 보이스피싱 등 다양한 사기 유형을 실시간으로 탐지하고, 사용자 커뮤니티를 통해 최신 사기 수법과 예방 정보를 공유하는 플랫폼입니다.

### 왜 S.Camp인가?

- 🚨 **실시간 AI 분석**: 의심스러운 URL이나 메시지를 즉시 분석
- 📰 **최신 뉴스**: 금융 사기 관련 최신 뉴스를 자동으로 수집
- 💬 **커뮤니티**: 실제 사기 사례와 예방 수칙을 공유
- 📱 **모바일 최적화**: 언제 어디서나 편리하게 사용

## ✨ 주요 기능

### 1. AI 사기 탐지기

- 입력한 URL 또는 메시지의 사기 위험도를 0-100점으로 분석
- 위험도에 따른 5단계로 구별되고, 각각의 단계에 따른 멘트를 제공
- 분석 결과와 함께 관련 사례 제공

### 2. 실시간 사기 뉴스

- 금융 사기 관련 최신 뉴스 자동 수집
- 키워드 기반 이모지 자동 매칭
- 외부 뉴스 사이트로 바로 연결

### 3. 사기 사례 게시판

- 카테고리별 필터링 (공지사항/예방수칙/사례공유)
- 게시글 상세 조회 및 공유 기능
- 조회수 추적 및 최신순을 오름차순 정렬

## 🛠 기술 스택

### Frontend

- **React 19.1.1** - UI 라이브러리
- **React Router DOM 7.9.5** - 클라이언트 사이드 라우팅
- **Vite 7.1.14** - 빌드 도구 및 개발 서버
- **Axios 1.13.1** - HTTP 클라이언트

### Styling

- **Vanilla CSS** - 커스텀 CSS (CSS 모듈 패턴)
- **lucide-react** - 아이콘 라이브러리

### Development Tools

- **Yarn** - 패키지 매니저

## 🚀 시작하기

### 필수 요구사항

- Node.js 18.0 이상
- Yarn 1.22 이상

### 설치 및 실행

1. **저장소 클론**

```bash
git clone https://github.com/kss2002/ganzi.git
cd ganzi
```

2. **의존성 설치**

```bash
yarn install
```

3. **개발 서버 실행**

```bash
yarn dev
```

4. **브라우저에서 확인**

```
http://localhost:5173
```

### 빌드

프로덕션 빌드를 생성하려면:

```bash
yarn build
```

빌드된 파일은 `dist/` 디렉토리에 생성됩니다.

### 프리뷰

빌드된 프로덕션 파일을 로컬에서 미리보기:

```bash
yarn preview
```

## 📁 프로젝트 구조

```
src/
├── pages/              # 페이지 컴포넌트
│   ├── main/          # 메인 홈 페이지
│   ├── ai/            # AI 탐지기 페이지
│   ├── board/         # 게시판 목록 및 상세 페이지
│   ├── news/          # 뉴스 페이지
│   └── not/           # 404 페이지
├── components/         # 재사용 가능한 컴포넌트
│   ├── board/         # 게시판 관련 컴포넌트
│   └── news/          # 뉴스 관련 컴포넌트
├── layout/            # 레이아웃 컴포넌트
│   ├── Layout.jsx     # 메인 레이아웃
│   └── Header.jsx     # 공통 헤더
├── hooks/             # 커스텀 훅
│   ├── useAiAnalysis.js
│   └── useScrollTop.js
├── api/               # API 클라이언트
│   ├── apiClient.js   # Axios 인스턴스
│   ├── newsApi.js     # 뉴스 API
│   ├── postApi.js     # 게시글 API
│   ├── analyzeApi.js  # AI 분석 API
│   └── index.js       # API 통합 export
├── animation/         # 애니메이션 관련
│   ├── FadeInSection.jsx
│   └── useFadeInAnimation.jsx
├── route/             # 라우팅 설정
│   └── routeConfig.jsx
├── utils/             # 유틸리티 함수
│   └── errorHandler.js
├── App.jsx            # 앱 루트 컴포넌트
├── main.jsx           # 진입점
└── index.css          # 글로벌 스타일
```

## 📡 API 문서

### Base URL

```
Production: https://api.inwoo.store
Development: http://localhost:5173/api (Vite Proxy)
```

### 주요 엔드포인트

#### 1. AI 분석

```http
POST /api/analyze
Content-Type: application/json

{
  "text": "분석할 URL 또는 메시지"
}

Response:
{
  "score": 85,
  "analysis": "분석 결과 상세 설명"
}
```

#### 2. 뉴스 조회

```http
GET /api/news

Response:
{
  "items": [
    {
      "title": "뉴스 제목",
      "description": "뉴스 요약",
      "link": "뉴스 링크",
      "pubDate": "발행일"
    }
  ]
}
```

#### 3. 게시글 조회

```http
GET /api/posts                          # 전체 게시글
GET /api/posts/{id}                     # 게시글 상세
GET /api/posts/category/{category}      # 카테고리별 조회

Response:
{
  "id": 1,
  "title": "제목",
  "content": "내용",
  "category": "NOTICE",
  "authorName": "작성자",
  "displayDate": "2025.11.03",
  "viewCount": 123
}
```

자세한 API 문서는 [Swagger](https://api.inwoo.store/swagger-ui/index.html)에서 확인하세요.

## 🌐 배포

- Vercel 배포

## 🎨 코드 스타일 가이드

### CSS 규칙

- **네이밍**: BEM 규칙 적용 (`.block__element--modifier`)
- **컬러**: CSS 변수 사용 (`--primary-color`, `--text-color`)
- **반응형**: 모바일까지 고려

### React 규칙

- **컴포넌트**: 함수형 컴포넌트 사용
- **상태 관리**: useState, useEffect 등 React Hooks 활용
- **Props**: 구조 분해 할당 사용
- **파일명**: PascalCase (예: `BoardItem.jsx`)

## 🤝 기여하기

https://github.com/kss2002/SCamp/blob/main/CONTRIBUTING.md

## 📄 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

## 👥 팀

- **Frontend Developer**: [@kss2002](https://github.com/kss2002)
- **Frontend Developer**: [@tlsgud0](https://github.com/tlsgud0)

## 📞 문의

프로젝트에 대한 질문이나 제안이 있으시면 [Issues](https://github.com/kss2002/ganzi/issues)를 통해 알려주세요.

<div align="center">
  
**Made with ❤️ by S.Camp Team**

https://s-camp.vercel.app

</div>

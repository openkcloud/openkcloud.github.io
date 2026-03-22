# openKcloud Platform — 프로젝트 사이트

openKcloud 오픈소스 프로젝트의 공식 웹사이트 소스코드입니다. 프로젝트 소개, 기술 문서, 뉴스, 커뮤니티 게시판, 다운로드 페이지 등을 제공하는 SPA(Single Page Application) 구조의 정적 사이트입니다.

---

## 기술 스택

- **HTML5** — 단일 `index.html` 파일에 전체 페이지를 포함하는 SPA 구조
- **CSS3** — 외부 스타일시트 (`css/style.css`), CSS 커스텀 프로퍼티(변수) 기반 테마 시스템
- **Vanilla JavaScript** — 프레임워크 없이 순수 JS로 페이지 전환, 모달, 필터링 등 구현
- **Google Fonts** — Noto Sans KR, Space Mono, Bebas Neue, Space Grotesk

빌드 도구나 번들러 없이 정적 파일만으로 구성되어 있어 별도의 빌드 과정 없이 바로 배포할 수 있습니다.

---

## 디렉토리 구조

```
/
├── index.html          # 메인 HTML (전체 페이지 포함)
├── css/
│   └── style.css       # 전역 스타일시트
├── images              # 이미지 폴더 
├── js                  # 전역 자바스크립트 
└── README.md           # 프로젝트 사이트 설명 
```

---

## 페이지 구성

사이트는 하나의 HTML 파일 내에 6개의 페이지 섹션(`div.page`)으로 구성되어 있으며, JavaScript의 `showPage()` 함수를 통해 SPA 방식으로 전환됩니다.

### Home (`#page-home`)

메인 랜딩 페이지로 다음 영역을 포함합니다.

- **Hero 섹션** — 프로젝트 타이틀, 소개 문구, 다운로드/GitHub 버튼, 플랫폼 스택 다이어그램 (kcloud-mnt → kcloud-llm → kcloud-opt → kcloud-svc → AI반도체)
- **통계 바** — 서브모듈 수(6), 최신 릴리스(v0.1), 오픈소스(100%), Cloud Native(K8s)
- **주요 기능** — 6개 핵심 기능을 카드 그리드로 소개 (이기종 자원 관리, 오케스트레이션, 옵저버빌리티, 개방형 인터페이스, 비용 최적화, LLM 실행환경)
- **시스템 프레임워크** — 4개 프레임워크(kcloud-svc, kcloud-opt, kcloud-llm, kcloud-mnt)의 역할 및 소속 서브모듈 상세 설명
- **시스템 아키텍처** — 4계층 다이어그램(통합 관리 → AI 서비스 → 최적화 → 서비스 제공), 각 계층의 모듈 및 칩 구성을 시각적으로 표현
- **Footer** — 관련 링크(GitHub, YouTube, Facebook, X), Contact 정보

### Github (`#page-github`)

- GitHub 조직 링크 및 리포지토리 통계 (Repositories, Latest Release, License)
- 메인 리포지토리 카드 (설명, 태그, GitHub 링크)

### Overview (`#page-overview`)

사이드바 네비게이션 기반의 기술 문서 페이지입니다. 좌측 사이드바와 우측 본문 컨텐츠로 구성된 docs 레이아웃을 사용합니다.

- **시작하기** — 소개 (`doc-intro`), 릴리스 노트 (`doc-release`)
- **아키텍처** — 전체 구조 (`doc-arch`), 플랫폼 레이어 (`doc-platform-layer`)
- **프레임워크별 문서** — kcloud-svc, kcloud-opt, kcloud-llm, kcloud-mnt 각각의 개요

릴리스 노트 섹션에는 v0.1.0의 프레임워크별 신규 기능, 버그 수정, 알려진 이슈, Breaking Changes, 시스템 요구 사항, 향후 v0.1.5 계획이 포함되어 있습니다.

### News (`#page-news`)

뉴스 및 업데이트 페이지입니다.

- 카테고리 필터 탭 — 전체, 릴리스, 공지 & 블로그, 로드맵, 미디어
- 카드 그리드 형태의 뉴스 목록
- 클릭 시 슬라이드 드로어(`news-drawer`)로 상세 내용 표시

### Community (`#page-community`)

커뮤니티 게시판 페이지입니다.

- 게시판 카테고리 필터 — 전체, 공지, 질문
- 게시글 목록 (고정 게시글, 일반 게시글)
- 새 질문 작성 모달 (`modal-newpost`) — 닉네임, 제목, 관련 모듈, 태그, 내용 입력 폼
- 게시글 상세 모달 (`modal-thread-detail`)

### Download (`#page-download`)

- 최신 릴리스(v0.1.0) 다운로드 카드 — 릴리스 날짜, 라이선스, 요구 사항, Source tar.gz 링크
- 변경 이력(Changelog) — 모듈별 릴리스 항목 나열

---

## 주요 UI 컴포넌트

| 컴포넌트 | 설명 |
|---|---|
| `showPage(id)` | SPA 페이지 전환 (nav active 상태 동기화) |
| `setDoc(el, id)` | Overview 문서 사이드바 네비게이션 |
| `filterNews(btn, cat)` | 뉴스 카테고리 필터링 |
| `filterForum(btn, cat)` | 게시판 카테고리 필터링 |
| `openNewsDrawer(id)` / `closeNewsDrawer()` | 뉴스 상세 드로어 열기/닫기 |
| `openModal(id)` / `closeModal(id)` | 모달 다이얼로그 제어 |
| `openThreadDetail(id)` | 게시글 상세 모달 열기 |
| `submitNewPost()` | 새 질문 작성 폼 제출 |
| `toggleGroup(el)` | 사이드바 아코디언 토글 |
| `.reveal` | 스크롤 진입 시 등장 애니메이션 |

---

## 로컬 실행

빌드 과정 없이 정적 파일을 웹 서버로 서빙하면 됩니다.

```bash
# Python 내장 서버 사용
python3 -m http.server 8000

# 또는 Node.js 기반
npx serve .
```

브라우저에서 `http://localhost:8000` 으로 접속합니다.

---

## 배포

정적 사이트이므로 별도 빌드 없이 파일 전체를 웹 서버 또는 정적 호스팅 서비스에 업로드하면 됩니다. GitHub Pages, Netlify, Cloudflare Pages 등에서 바로 호스팅할 수 있습니다.

---

## 라이선스

Apache License 2.0

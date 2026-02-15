# 🌱 Quartz + GitHub Pages로 옵시디언 노트 무료 배포하기
> **대상:** 코딩을 몰라도 따라할 수 있는 완전 초보자 가이드
> **소요 시간:** 처음 설정 약 30~60분 | 이후 업데이트 명령어 1줄

---

## 📌 전체 흐름 먼저 이해하기

```
[내 컴퓨터 옵시디언]
        ↓  노트 작성
[Quartz가 HTML로 변환]
        ↓  명령어 1줄
[GitHub에 업로드]
        ↓  자동 빌드
[인터넷에서 누구나 접근 가능한 웹사이트]
```

쉽게 말하면, **옵시디언 = 원고지**, **Quartz = 출판사**, **GitHub Pages = 서점** 이다.

---

## 🛒 STEP 0 — 준비물 설치 (딱 3가지)

### 0-1. GitHub 계정 만들기
1. [github.com](https://github.com) 접속
2. 우측 상단 **Sign up** 클릭
3. 이메일·비밀번호·사용자명 입력 후 가입
   > ⚠️ **사용자명이 곧 내 사이트 주소가 됨!**
   > `홍길동` → 사이트 주소: `홍길동.github.io`
   > 영문·숫자·하이픈만 사용, 신중하게 정하기

---

### 0-2. Node.js 설치

1. [nodejs.org](https://nodejs.org) 접속
2. **LTS 버전** (왼쪽 버튼) 다운로드 클릭
3. 다운된 `.msi` 파일 실행 → 계속 **Next** → **Install**
4. 설치 완료 후 확인:
   - **Windows 키** 누르고 `cmd` 검색 → **명령 프롬프트** 실행
   - 아래 입력 후 엔터:
     ```
     node -v
     ```
   - `v20.x.x` 같은 버전 숫자가 뜨면 ✅ 성공

---

### 0-3. Git 설치

1. [git-scm.com](https://git-scm.com) 접속
2. **Download for Windows** 클릭
3. 다운된 파일 실행 → 모든 옵션 기본값 유지하며 **Next** → **Install**
4. 설치 확인:
   ```
   git -v
   ```
   - `git version 2.x.x` 숫자가 뜨면 ✅ 성공

> 💡 **명령 프롬프트(cmd)** 가 뭔지 모르겠다면?
> Windows 키 → `cmd` 검색 → 검정 창이 뜨는 것. 여기에 명령어를 입력하면 컴퓨터가 작업을 수행한다.

---

## 🍴 STEP 1 — Quartz 가져오기 (GitHub Fork)

**Fork = 남의 프로그램을 내 계정으로 복사해오는 것**

1. [github.com/jackyzha0/quartz](https://github.com/jackyzha0/quartz) 접속
2. 우측 상단 **Fork** 버튼 클릭

   ```
   ┌─────────────────────────────────────────┐
   │  jackyzha0 / quartz          ⭐ Star  🍴 Fork  │
   └─────────────────────────────────────────┘
   ```

3. Fork 설정 화면에서:
   - **Repository name**: `quartz` 그대로 두거나 원하는 이름 입력
     (나중에 바꿀 수 있음)
   - **Copy the `v4` branch only** 체크박스 ✅ 체크
   - **Create fork** 클릭

4. 잠시 후 내 계정에 `나의ID/quartz` 저장소가 생성됨 ✅

---

## 💻 STEP 2 — 내 컴퓨터로 가져오기 (Clone)

**Clone = GitHub에 있는 파일을 내 컴퓨터로 복사해오는 것**

1. 방금 만든 내 저장소 페이지에서 초록색 **Code** 버튼 클릭
2. **HTTPS** 탭의 주소 복사 (예: `https://github.com/나의ID/quartz.git`)

3. 명령 프롬프트(cmd) 열기
4. 파일을 저장할 폴더로 이동 (예: 바탕화면):
   ```
   cd %USERPROFILE%\Desktop
   ```
ls
5. Clone 실행 (복사한 주소 붙여넣기):
   ```
   git clone https://github.com/나의ID/quartz.git
   ```

6. 완료되면 바탕화면에 `quartz` 폴더가 생김 ✅

---

## 📦 STEP 3 — Quartz 설치

1. quartz 폴더로 이동:
   ```
   cd quartz
   ```

2. 필요한 프로그램 설치 (인터넷 연결 필요, 1~3분 소요):
   ```
   npm i
   ```

   > 뭔가 쭉 설치되는 메시지가 뜨면 정상. 빨간 에러 없이 끝나면 ✅

3. Quartz 초기화:
   ```
   npx quartz create
   ```

   > 질문이 뜨면 그냥 **엔터** 눌러서 기본값 선택

---

## 🔗 STEP 4 — 옵시디언 Vault 연결하기

**방법 A: 복사 방식 (초보자 추천 ✅)**

`quartz` 폴더 안에 `content` 폴더가 있다.
여기에 옵시디언 노트(.md 파일)를 복사·붙여넣기 하면 된다.

```
📁 quartz
  └── 📁 content        ← 여기에 노트를 넣는다
        ├── index.md    ← 사이트 첫 화면 (메인 페이지)
        ├── 증시시황_2026-W07.md
        └── 📁 투자분석
              └── AI섹터분석.md
```

> 💡 **index.md가 사이트 첫 화면**이 된다. 반드시 하나 만들어두자.
> 아래를 복사해서 `content/index.md` 로 저장:
> ```markdown
> # 나의 투자 노트
> 안녕하세요! 주간 증시 시황 분석 노트를 공유합니다.
> ```

**방법 B: 심볼릭 링크 방식 (자동 동기화)**

옵시디언 Vault 폴더와 `content` 폴더를 연결해두면,
옵시디언에서 저장할 때 자동으로 반영된다.

```
mklink /D "C:\Desktop\quartz\content" "C:\Users\나\Documents\ObsidianVault"
```

> ⚠️ 경로는 본인 환경에 맞게 수정 필요

---

## ⚙️ STEP 5 — 사이트 기본 설정

`quartz` 폴더 안의 `quartz.config.ts` 파일을 메모장으로 열기.

> quartz 폴더 → `quartz.config.ts` 파일 우클릭 → 연결 프로그램 → 메모장

아래 항목만 찾아서 수정하면 된다:

```typescript
const config: QuartzConfig = {
  configuration: {
    pageTitle: "나의 투자 노트",              // ← 사이트 이름
    pageTitleSuffix: " | 주간 시황",          // ← 탭에 표시될 접미사
    enableSPA: true,
    enablePopovers: true,
    analytics: null,
    locale: "ko-KR",                          // ← 한국어 설정
    baseUrl: "나의ID.github.io",              // ← 내 GitHub 사용자명.github.io
    ignorePatterns: ["private", ".obsidian"], // ← private 폴더는 비공개
    ...
  }
}
```

> 💡 `private` 폴더를 만들어두면 그 안의 노트는 웹에 올라가지 않는다.
> 공개하고 싶지 않은 노트는 `content/private/` 폴더에 넣으면 된다.

저장 후 닫기 ✅

---

## 🔍 STEP 6 — 로컬에서 미리보기

인터넷에 올리기 전에 내 컴퓨터에서 먼저 확인해보자.

```
npx quartz build --serve
```

- 실행 후 브라우저에서 [http://localhost:8080](http://localhost:8080) 접속
- 실제 사이트 모습이 그대로 보인다 ✅
- 확인 후 `Ctrl + C` 로 종료

---

## 🚀 STEP 7 — GitHub Pages 활성화하기

### 7-1. GitHub Actions 권한 설정

1. 내 GitHub 저장소 (`github.com/나의ID/quartz`) 접속
2. 상단 탭 **Settings** 클릭
3. 왼쪽 메뉴 → **Actions** → **General**
4. 아래 스크롤 → **Workflow permissions** 에서
   **Read and write permissions** 선택 ✅
5. **Save** 클릭

### 7-2. GitHub Pages 소스 설정

1. 왼쪽 메뉴 → **Pages** 클릭
2. **Source** 드롭다운 → **GitHub Actions** 선택
3. 저장

---

## 📤 STEP 8 — 인터넷에 배포하기!

드디어 마지막 단계! 명령어 3줄이면 끝.

```
npx quartz sync --no-pull
```

> 이 명령어 하나가:
> 1. 빌드 (마크다운 → HTML 변환)
> 2. GitHub에 업로드
> 3. 자동 배포
> 를 모두 처리해준다!

약 2~3분 후 아래 주소로 접속:
```
https://나의ID.github.io/quartz
```

🎉 **내 옵시디언 노트가 웹사이트로 공개됨!**

---

## 🔄 STEP 9 — 앞으로 노트 업데이트하는 법

새 노트를 추가하거나 수정했을 때는 딱 이것만:

```
cd %USERPROFILE%\Desktop\quartz
npx quartz sync
```

**끝!** 2~3분 후 사이트에 자동 반영된다.

---

## 🎨 STEP 10 — 사이트 꾸미기 (선택사항)

### 테마 색상 변경
`quartz/styles/custom.scss` 파일에서 색상 변경 가능:

```scss
:root {
  --light: #faf8f8;       /* 배경색 */
  --dark: #141021;        /* 글자색 */
  --secondary: #84a59d;   /* 링크색 */
  --tertiary: #f28482;    /* 강조색 */
  --highlight: rgba(143, 188, 187, 0.15); /* 하이라이트 */
}
```

### 사이트 레이아웃 변경
`quartz.layout.ts` 에서 사이드바 위치, 목차 표시 등 조정 가능.

### 추천 플러그인 설정 (quartz.config.ts)
```typescript
plugins: {
  transformers: [
    Plugin.FrontMatter(),          // YAML 읽기
    Plugin.ObsidianFlavoredMarkdown({ enableInHtmlEmbed: false }),
    Plugin.GitHubFlavoredMarkdown(),
    Plugin.TableOfContents(),      // 목차 자동생성
    Plugin.CrawlLinks({ markdownLinkResolution: 'shortest' }),
    Plugin.Description(),
    Plugin.Latex({ renderEngine: 'katex' }),  // 수식
  ],
  filters: [Plugin.RemoveDrafts()],  // draft: true 노트 제외
  emitters: [
    Plugin.AliasRedirects(),
    Plugin.ComponentResources(),
    Plugin.ContentPage(),
    Plugin.FolderPage(),
    Plugin.TagPage(),
    Plugin.ContentIndex({
      enableSiteMap: true,    // SEO용 사이트맵
      enableRSS: true,        // RSS 피드 자동생성
    }),
  ],
}
```

---

## ❓ 자주 겪는 문제 & 해결법

| 문제 | 원인 | 해결 |
|------|------|------|
| `node` 명령어를 못 찾겠다 | Node.js 설치 후 cmd 재시작 필요 | cmd 닫고 다시 열기 |
| 사이트가 비어있다 | content 폴더에 파일이 없음 | .md 파일을 content 폴더에 넣기 |
| 한글 파일명이 깨진다 | URL 인코딩 문제 | 파일명을 영문으로 변경 추천 |
| 이미지가 안 보인다 | 이미지 경로 문제 | 이미지를 `content/assets/` 폴더에 넣고 경로 수정 |
| 위키링크가 안 된다 | Obsidian 플러그인 미설정 | `quartz.config.ts` 에서 `ObsidianFlavoredMarkdown` 플러그인 확인 |
| 사이트가 업데이트 안 됨 | push를 안 했을 가능성 | `npx quartz sync` 재실행 |
| GitHub Actions가 실패 | 권한 설정 누락 | STEP 7-1 권한 설정 재확인 |

---

## 💡 알아두면 좋은 꿀팁

### 공개/비공개 노트 분리
```
📁 content
  ├── 📁 public           ← 공개 노트
  │     └── 증시시황.md
  └── 📁 private          ← 비공개 (웹에 안 올라감)
        └── 개인일기.md
```
`quartz.config.ts` 에 `ignorePatterns: ["private"]` 설정 필수!

### 노트에 draft 설정
```yaml
---
draft: true    ← 이 노트는 웹에 공개 안 됨
---
```

### 커스텀 도메인 연결 (선택)
가비아·Namecheap 등에서 도메인 구매 후 GitHub Pages Settings → Custom domain에 입력하면 `mysite.com` 형태로 접속 가능.

### RSS 피드 활용
`https://나의ID.github.io/quartz/index.xml` 주소로 RSS가 자동 생성됨. 구독자들이 RSS 리더로 새 글 알림 받을 수 있다.

---

## 🗺️ 전체 과정 요약 체크리스트

- [ ] GitHub 계정 생성
- [ ] Node.js 설치 확인 (`node -v`)
- [ ] Git 설치 확인 (`git -v`)
- [ ] Quartz Fork
- [ ] Clone (`git clone ...`)
- [ ] `npm i` 설치
- [ ] `npx quartz create`
- [ ] content 폴더에 노트 넣기
- [ ] index.md 생성
- [ ] quartz.config.ts 에서 baseUrl 수정
- [ ] 로컬 미리보기 (`npx quartz build --serve`)
- [ ] GitHub Actions 권한 설정
- [ ] GitHub Pages 소스 → GitHub Actions 설정
- [ ] `npx quartz sync --no-pull` 로 첫 배포
- [ ] `https://나의ID.github.io/quartz` 접속 확인 🎉

---

*참고: [Quartz 공식 문서](https://quartz.jzhao.xyz) | [GitHub Pages 문서](https://docs.github.com/pages)*

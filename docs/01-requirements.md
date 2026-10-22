# 포트폴리오 사이트와 GitHub 프로필 README requirements

이 문서는 pokavv의 포트폴리오 사이트와 GitHub 프로필 README를 새로 만들기 전에 두 결과물이 보여 줄 내용, 지켜야 할 보안과 성능 기준, 제약 조건을 정하는 requirements analysis 단계의 deliverable이다. deliverable은 단계마다 만들어 사용자에게 검토받는 문서다. 다음 단계인 architecture design은 여기서 정한 내용을 기준으로 진행된다.

아래에서 '사용자'는 사이트와 README를 관리하는 pokavv이고, '방문자'는 두 결과물을 보는 사람이다.

## 1. 범위

### 1.1 포트폴리오 사이트

- 저장소: 공개 저장소 pokavv/pokavv.github.io
- 로컬 저장소: C:\my\portfolio
- 주소: https://pokavv.github.io
- 배포: GitHub Pages
- 공개 범위: 이 저장소에 commit하는 사이트 소스와 docs/의 설계 문서는 모두 공개된다.

GitHub Pages는 GitHub 저장소의 HTML, CSS, JavaScript 파일을 가져와 필요하면 빌드 과정을 거친 뒤 웹사이트로 publish하는 정적 사이트 호스팅 서비스다(출처: https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages). 같은 문서에 따르면 user site의 소스 파일은 `<owner>.github.io` 저장소에 두어야 하고, 사이트의 기본 주소는 `http(s)://<owner>.github.io`다(출처: https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages). 여기서 `<owner>`는 계정 이름이다. 그래서 이 사이트의 저장소 이름은 pokavv.github.io이고 주소는 https://pokavv.github.io다.

### 1.2 GitHub 프로필 README

- 저장소: 공개 저장소 pokavv/pokavv
- 표시 위치: https://github.com/pokavv 프로필 화면
- 로컬 사본: C:\my\portfolio\profile

프로필 README는 `<계정 이름>/<계정 이름>` 저장소에 든 README.md이고, GitHub는 이 파일을 계정의 프로필 화면에 보여 준다. GitHub 문서에 따르면 아래 네 조건을 모두 만족할 때 프로필 화면에 프로필 README가 표시된다(출처: https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme).

1. 저장소 이름이 계정 이름과 같다.
2. 저장소가 공개 저장소다.
3. 저장소 루트에 README.md 파일이 있다.
4. README.md 파일에 내용이 있다.

프로필 README.md를 처음 쓸 때 pokavv/pokavv 저장소를 만든다. 이 저장소의 로컬 사본은 C:\my\portfolio\profile 폴더에 둔다. 사이트 저장소의 .gitignore에는 `/profile/`을 적어서, git이 이 폴더를 추적하지 않게 한다. .gitignore에는 git이 추적하지 않을 파일과 폴더의 경로를 적는다.

### 1.3 범위 밖

- 블로그 글 작성 기능
- 방명록과 댓글처럼 방문자가 쓰는 기능
- 서버 프로그램
- 관리자 화면

## 2. User scenario

방문자와 사용자가 두 결과물을 보거나 고치는 경우는 아래 다섯 가지다.

- 사이트 열람: 방문자가 PC나 휴대폰 브라우저로 https://pokavv.github.io를 열어 소개, 기술, 프로젝트, 경력, 연락처를 본다.
- 프로젝트 상세 열람: 방문자가 프로젝트 하나를 골라 그 프로젝트의 상세 페이지에서 3.2절 '프로젝트 항목'에 적힌 항목을 모두 본다.
- 프로필 열람: 방문자가 https://github.com/pokavv를 열어 짧은 소개, 주요 기술, 대표 프로젝트, 포트폴리오 사이트 링크를 본다.
- 내용 수정과 재배포: 사용자가 저장소의 내용 파일을 고쳐 push하면 사이트가 다시 배포된다. 배포 방식은 architecture design에서 정한다.
- 프로필 README 수정: 사용자가 C:\my\portfolio\profile의 README.md를 고쳐 pokavv/pokavv에 push하면 https://github.com/pokavv 프로필 화면에 바뀐 내용이 표시된다.

## 3. 보여 줄 내용

### 3.1 사이트 section

사이트는 아래 다섯 section으로 이루어진다.

| section | 보여 줄 내용 |
|---|---|
| 소개 | 표시 이름, 하는 일, 한 줄 소개 |
| 기술 | 언어, framework, infra 도구 |
| 프로젝트 | 프로젝트 목록과 프로젝트별 상세 |
| 경력 | 회사, 기간, 맡은 일 |
| 연락처 | GitHub 링크, 이메일(사용자가 정한 경우만) |

### 3.2 프로젝트 항목

프로젝트 목록에는 이름, 한 줄 설명, 쓴 기술, 상태를 보여 주고, 프로젝트 상세 페이지에는 아래 항목을 모두 보여 준다.

- 이름
- 한 줄 설명
- 설명: 한 줄 설명보다 자세한 여러 문단의 설명
- 기간
- 쓴 기술
- 맡은 일
- 상태: 진행 중, 완료, 중단 가운데 하나
- 공개 링크: 있을 때만

### 3.3 프로필 README

프로필 README에는 짧은 소개, 주요 기술, 대표 프로젝트 몇 개, 포트폴리오 사이트 링크를 넣는다. 통계 카드나 badge처럼 외부 서비스가 만드는 이미지를 넣을지는 detailed design에서 정한다.

### 3.4 내용 출처

사이트와 README의 내용은 pokavv의 GitHub 저장소에 있는 이름, 설명, 언어, 문서를 바탕으로 쓴다. 경력과 이름 표기처럼 저장소에 없는 내용은 사용자에게 받는다(8절 '사용자에게 받을 내용').

## 4. Scale

사이트는 메인 페이지와 프로젝트 상세 페이지로 이루어지고, 소개할 프로젝트는 20개 이하다.

GitHub 문서에 따르면 publish된 GitHub Pages 사이트의 크기는 1 GB를 넘을 수 없고, 대역폭에는 월 100 GB의 soft limit이 있다(출처: https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits). 같은 문서에 따르면 사이트가 이 두 한도를 넘으면 GitHub가 사이트를 제공하지 못하거나, GitHub Support가 이 사이트 때문에 GitHub 서버에 생기는 부하를 줄이는 방법을 이메일로 안내할 수 있다(출처: https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits). 사이트 파일의 전체 크기는 1 GB 이하여야 하고 배포할 때마다 이 크기를 확인한다. 대역폭 사용량을 확인하는 방법은 architecture design에서 정한다.

## 5. Security

아래 규칙은 공개 저장소 두 곳(pokavv/pokavv.github.io, pokavv/pokavv)에 commit하는 모든 파일과 commit 메시지에 적용한다. docs/의 설계 문서도 사이트 저장소에 들어 있어서 공개되므로 같은 규칙을 따른다.

- 공개 저장소에 토큰, 비밀번호, 개인 키 같은 secret을 넣지 않는다.
- 비공개 저장소의 코드, 내부 문서 원문, 저장소 링크를 넣지 않는다. 비공개 저장소의 이름, 설명, 개수는 사용자가 8절 '사용자에게 받을 내용'에서 공개를 허락한 범위만 넣는다.
- 회사 내부 정보를 넣지 않는다. 사내 서버 주소, 내부 시스템 이름, 계정, 고객 정보가 여기에 해당한다.
- 전화번호와 집 주소를 넣지 않는다. 이메일은 사용자가 정한 주소만 넣는다.
- commit의 author와 committer는 pokavv의 noreply 주소인 `pokavv <109390318+pokavv@users.noreply.github.com>`으로 기록한다. noreply 주소는 GitHub가 계정마다 만들어 주는 commit용 이메일 주소다. GitHub 웹 화면에서 만든 commit의 author 이메일은 계정의 'Keep my email addresses private' 설정에 따라 정해진다(출처: https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address). 그래서 이 설정이 켜져 있는지 확인하기 전에는 웹 화면에서 파일을 고치지 않는다. 그래야 개인 이메일과 회사 이메일이 공개 저장소의 commit 기록에 남지 않는다.
- 방문자 추적 스크립트, 외부 analytics, 광고를 넣지 않는다. analytics는 방문자의 접속 기록을 모아 통계로 보여 주는 서비스다.
- 프로필 README에 넣는 외부 이미지(통계 카드, badge)는 공개 저장소의 정보만 보여 준다. 비공개 저장소를 읽을 수 있는 토큰을 외부 서비스나 GitHub Actions에 주지 않고, 방문 횟수를 세는 이미지는 넣지 않는다.

## 6. Performance targets

### 6.1 Lighthouse 점수

배포된 사이트의 메인 페이지와 모든 프로젝트 상세 페이지를 Lighthouse 모바일 설정으로 페이지마다 5번 측정하고, Performance, Accessibility, Best Practices, SEO(Search Engine Optimization) 점수의 중앙값이 각각 90 이상이어야 한다. Lighthouse는 웹페이지를 검사해 category별 점수를 0~100으로 매긴다. 측정에 쓴 도구, Lighthouse 버전, 측정한 날짜는 결과와 함께 기록한다. Lighthouse 문서에 따르면 코드가 바뀌지 않아도 Performance 점수는 측정마다 달라질 수 있고, 5번 측정한 중앙값은 1번 측정한 값보다 두 배 안정적이다(출처: https://github.com/GoogleChrome/lighthouse/blob/main/docs/variability.md).

Lighthouse 문서에 따르면 Performance 점수는 0~49가 Poor, 50~89가 Needs Improvement, 90~100이 Good으로 표시된다(출처: https://developer.chrome.com/docs/lighthouse/performance/performance-scoring). 같은 문서는 좋은 사용자 경험을 주려면 사이트가 Good 점수(90~100)를 목표로 해야 한다고 설명한다(출처: https://developer.chrome.com/docs/lighthouse/performance/performance-scoring). 이 requirements 문서는 Performance의 Good 하한인 90점을 나머지 세 category에도 같은 목표로 적용한다.

### 6.2 Core Web Vitals

web.dev 문서에 따르면 Core Web Vitals는 Google이 Web Vitals initiative로 제시한 지표 가운데 모든 웹페이지에 적용되는 지표이고, 지금은 아래 표의 세 지표로 이루어진다(출처: https://web.dev/articles/vitals). 표의 기준값은 모두 같은 문서에 적힌 값이다(출처: https://web.dev/articles/vitals).

| 지표 | 측정 대상 | good 기준 |
|---|---|---|
| LCP(Largest Contentful Paint) | 로딩 성능 | 페이지가 처음 로드되기 시작한 때부터 2.5초 이내 |
| INP(Interaction to Next Paint) | 상호작용성 | 200 ms 이하 |
| CLS(Cumulative Layout Shift) | 시각적 안정성 | 0.1 이하 |

web.dev 문서에 따르면 Lighthouse는 방문자의 입력 없이 페이지를 불러오므로 INP를 측정하지 못한다(출처: https://web.dev/articles/vitals). 그 문서는 lab에서 잴 수 있는 TBT(Total Blocking Time)를 INP 대신 확인하는 지표로 소개한다(출처: https://web.dev/articles/vitals). lab 측정은 실제 방문자 없이 도구가 페이지를 불러와 값을 재는 방법이다. TBT는 페이지가 클릭, 탭, 키 입력에 응답할 수 없게 막혀 있던 시간을 모두 더한 값이다(출처: https://developer.chrome.com/docs/lighthouse/performance/lighthouse-total-blocking-time). LCP, CLS, TBT는 6.1절 'Lighthouse 점수'의 5번 측정에서 나온 값으로 판정한다. 페이지마다 LCP와 CLS의 중앙값은 위 표의 good 기준을 만족해야 하고, TBT의 중앙값은 Lighthouse 모바일 기준 Green(fast) 범위인 200 ms 이하여야 한다(출처: https://developer.chrome.com/docs/lighthouse/performance/lighthouse-total-blocking-time).

web.dev 문서는 방문자 대부분이 표의 기준을 경험하는지 확인하려면 page load의 75th percentile 값을 모바일과 데스크톱으로 나누어 측정하라고 권한다(출처: https://web.dev/articles/vitals). 75th percentile은 측정값을 작은 값부터 차례로 늘어놓았을 때 75% 위치에 있는 값이다. CrUX(Chrome User Experience Report)는 Chrome 사용자의 실제 측정값을 모은 Google의 데이터다(출처: https://developer.chrome.com/docs/crux). CrUX 문서에 따르면 방문자가 일정 수에 못 미치는 페이지는 CrUX 데이터에 들어가지 않고, 그 수는 공개되지 않는다(출처: https://developer.chrome.com/docs/crux/methodology). PageSpeed Insights는 페이지의 사용자 경험을 모바일과 데스크톱으로 나누어 보고하는 도구이고, 실제 방문자의 측정값을 CrUX에서 가져온다(출처: https://developers.google.com/speed/docs/insights/v5/about). 그래서 6.1절의 측정을 할 때마다 PageSpeed Insights도 열어 보고, 이 사이트의 CrUX 데이터가 나올 때만 75th percentile 기준을 확인한다. PageSpeed Insights가 보여 주는 실제 방문자의 측정값은 지난 28일 동안 모은 값이다(출처: https://developers.google.com/speed/docs/insights/v5/about). 데이터가 나오면 모바일과 데스크톱 각각에서 LCP, INP, CLS의 75th percentile 값이 위 표의 good 기준을 모두 만족해야 한다(출처: https://web.dev/articles/vitals). 페이지 단위 데이터가 부족할 때 PageSpeed Insights가 대신 보여 주는 origin 단위 데이터는 사이트의 모든 페이지에서 모은 값이고, 이때는 그 값으로 판정한다(출처: https://developers.google.com/speed/docs/insights/v5/about).

## 7. Constraints

- GitHub 요금제: pokavv 계정은 GitHub Free 요금제를 쓴다. 2026-10-22에 GitHub API `GET /user` 응답의 `plan.name` 값이 `free`인 것을 확인했다. GitHub 문서에 따르면 저장소를 가진 계정이 GitHub Free 요금제를 쓰면 Pages 사이트를 만들 저장소는 공개 저장소여야 한다(출처: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site). 그래서 사이트 저장소는 공개 저장소로 만든다.
- 정적 사이트: 정적 파일만 배포하고 서버 프로그램과 데이터베이스는 두지 않는다. GitHub Pages는 정적 사이트 호스팅 서비스다(출처: https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages).
- publish 범위: 사이트를 이루는 파일만 https://pokavv.github.io에 publish하고, docs/의 설계 문서는 저장소에만 둔다. 이 조건을 지키는 배포 방식은 architecture design에서 정한다.
- 비용: 0원으로 유지한다. GitHub 문서에 따르면 GitHub Actions는 공개 저장소에서 무료다(출처: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).
- 화면 폭: 360px~1920px에서 가로 스크롤 없이 보여야 한다.
- 테마: 밝은 테마와 어두운 테마를 지원하고 기본값은 운영 체제 설정을 따른다.
- 언어: 한국어
- 지원 브라우저: 확인하는 날의 최신 안정 버전인 PC의 Chrome, Edge, Safari, Firefox와 휴대폰의 Chrome, Safari. 확인한 브라우저와 버전은 결과와 함께 기록한다.

## 8. 사용자에게 받을 내용

아래 내용은 저장소에 없으므로 사용자에게 받는다.

- 사이트와 README에 쓸 이름 표기
- 경력: 회사, 기간, 맡은 일
- 넣을 프로젝트와 뺄 프로젝트, 프로젝트마다 공개할 범위
- 연락처로 공개할 이메일. 사용자가 정하지 않으면 연락처에는 GitHub 링크만 넣는다.

## 출처

2026-10-22에 아래 자료의 원문을 받아 인용한 문장을 확인했다.

- GitHub Docs, What is GitHub Pages?: https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages
- GitHub Docs, Creating a GitHub Pages site: https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- GitHub Docs, GitHub Pages limits: https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits
- GitHub Docs, Managing your profile README: https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme
- GitHub Docs, Setting your commit email address: https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address
- Chrome for Developers, Lighthouse performance scoring: https://developer.chrome.com/docs/lighthouse/performance/performance-scoring
- Chrome for Developers, Total Blocking Time: https://developer.chrome.com/docs/lighthouse/performance/lighthouse-total-blocking-time
- Lighthouse, Score Variability: https://github.com/GoogleChrome/lighthouse/blob/main/docs/variability.md
- web.dev, Web Vitals: https://web.dev/articles/vitals
- Chrome for Developers, Overview of CrUX: https://developer.chrome.com/docs/crux
- Chrome for Developers, CrUX methodology: https://developer.chrome.com/docs/crux/methodology
- Google for Developers, About PageSpeed Insights: https://developers.google.com/speed/docs/insights/v5/about

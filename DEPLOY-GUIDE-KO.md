# Yong-chan Park 홈페이지 배포 안내

이 폴더는 **B형 Compact Profile 헤더를 적용한 정적 GitHub Pages 홈페이지**입니다.

- 별도의 빌드 도구, npm, Ruby, Jekyll 설치가 필요하지 않습니다.
- 기존 주소 `https://yongchanpark.github.io/`를 그대로 사용합니다.
- 프로필 사진은 항상 1:1 정사각형으로 표시됩니다.
- `Y` 이니셜의 둥근 사각형 favicon이 필요한 형식별로 포함되어 있습니다.

---

## 먼저 답: 기존 홈페이지를 덮어쓸 수 있나요?

**네. 가능합니다.**

GitHub Pages는 지정된 브랜치와 폴더의 파일을 웹사이트로 배포합니다. 현재 사이트에 사용 중인 `gh-pages` 브랜치의 루트에 새 파일을 커밋하고 푸시하면, 같은 주소인 `https://yongchanpark.github.io/`에 새 디자인이 게시됩니다.

다만 “덮어쓰기”에는 두 가지가 있습니다.

1. **같은 이름의 파일**  
   예: `favicon.ico`  
   새 파일로 교체됩니다.

2. **새 패키지에 없는 예전 파일**  
   예: `_layouts/`, `_includes/`, `index.md`  
   자동으로 삭제되지는 않고 저장소에 남습니다.

새 홈페이지에는 `index.html`과 `.nojekyll`이 포함되어 있어 예전 Jekyll 테마 파일이 남아 있어도 새 사이트를 배포할 수 있습니다. 저장소까지 깔끔하게 정리하려면 아래의 **GitHub Desktop 방법**을 권장합니다.

---

# 배포 전에 할 일

## 1. 패키지 압축 풀기

`yongchan-github-pages-final.zip`의 압축을 풉니다.

압축을 풀면 다음과 같은 폴더가 나옵니다.

```text
yongchan-github-pages-final/
├── index.html
├── styles.css
├── site.js
├── 404.html
├── .nojekyll
├── favicon.svg
├── favicon.ico
├── favicon-16x16.png
├── favicon-32x32.png
├── apple-touch-icon.png
├── android-chrome-192x192.png
├── android-chrome-512x512.png
├── site.webmanifest
├── sitemap.xml
├── robots.txt
├── assets/
│   └── profile.jpg
├── README.md
└── DEPLOY-GUIDE-KO.md
```

## 2. 프로필 사진 교체

1. 사용할 사진을 준비합니다.
2. 파일 이름을 정확히 `profile.jpg`로 바꿉니다.
3. 패키지의 `assets/profile.jpg`를 새 사진으로 교체합니다.
4. 권장 크기는 `800 × 800px` 이상입니다.
5. 파일 용량은 가능하면 1MB 이하로 줄이는 것이 좋습니다.

사진이 정사각형이 아니어도 CSS가 중앙을 기준으로 1:1로 잘라 표시합니다. 다만 얼굴이 사진 중앙에 오도록 미리 정리하면 더 자연스럽습니다.

---

# 방법 1 — GitHub Desktop으로 깔끔하게 교체하기

가장 안전하고 이해하기 쉬운 방법입니다. 기존 자료 폴더를 보존하면서 예전 테마 파일도 함께 정리할 수 있습니다.

## 1단계. 현재 사이트 백업

가장 간단한 백업 방법은 다음과 같습니다.

1. GitHub에서 `YongchanPark/YongchanPark.github.io` 저장소를 엽니다.
2. 브랜치 메뉴에서 `gh-pages`를 선택합니다.
3. `Code` 버튼을 누릅니다.
4. `Download ZIP`을 눌러 현재 저장소를 보관합니다.

이 ZIP은 문제가 생겼을 때 원래 홈페이지로 되돌리는 용도입니다.

## 2단계. 저장소를 GitHub Desktop으로 내려받기

1. GitHub Desktop을 실행하고 GitHub 계정으로 로그인합니다.
2. 브라우저에서 `YongchanPark/YongchanPark.github.io` 저장소를 엽니다.
3. `Code` → `Open with GitHub Desktop`을 누릅니다.
4. 컴퓨터에 저장할 위치를 선택하고 `Clone`을 누릅니다.
5. GitHub Desktop 상단의 `Current Branch`가 `gh-pages`인지 확인합니다.
6. 다른 브랜치라면 `Current Branch`를 눌러 `gh-pages`로 전환합니다.

## 3단계. 기존 `resources/` 폴더 보존하기

클론한 저장소 폴더에는 기존 논문, CV, BibTeX, 발표 자료가 들어 있는 `resources/` 폴더가 있습니다.

**이 폴더는 삭제하지 마세요.**

```text
resources/
```

새 홈페이지의 Paper, BibTeX, Slides, CV 링크가 이 폴더를 사용합니다.

## 4단계. 예전 테마 파일 정리

GitHub Desktop에서 `Repository` → `Show in Finder` 또는 `Show in Explorer`를 눌러 저장소 폴더를 엽니다.

다음 예전 Jekyll 테마 파일과 폴더는 삭제해도 됩니다.

```text
_config.yml
index.md
_includes/
_layouts/
assets/css/
icons/
```

아래 항목은 유지합니다.

```text
.git/
resources/
```

`assets/` 폴더 자체는 남겨 두어도 되고, `assets/css/`만 삭제해도 됩니다. 새 패키지의 `assets/profile.jpg`가 이 폴더에 들어갑니다.

## 5단계. 새 홈페이지 파일 복사

1. 압축을 푼 `yongchan-github-pages-final` 폴더를 엽니다.
2. **폴더 자체가 아니라 그 안의 파일과 폴더 전체**를 선택합니다.
3. 클론한 `YongchanPark.github.io` 저장소의 최상위 폴더에 복사합니다.
4. 같은 이름의 파일을 바꿀지 묻는 창이 나오면 교체를 선택합니다.

최종 구조에서 `index.html`이 저장소 루트에 직접 보여야 합니다.

올바른 구조:

```text
YongchanPark.github.io/
├── index.html
├── styles.css
├── favicon.svg
├── assets/
├── resources/
└── ...
```

잘못된 구조:

```text
YongchanPark.github.io/
└── yongchan-github-pages-final/
    └── index.html
```

## 6단계. 커밋하고 GitHub에 올리기

1. GitHub Desktop으로 돌아갑니다.
2. 왼쪽에 변경된 파일 목록이 표시되는지 확인합니다.
3. 왼쪽 아래 `Summary`에 다음처럼 입력합니다.

```text
Redesign academic homepage
```

4. `Commit to gh-pages`를 누릅니다.
5. 상단의 `Push origin`을 누릅니다.

이 시점에 같은 저장소와 같은 주소에 새 홈페이지가 올라갑니다.

## 7단계. GitHub Pages 설정 확인

1. GitHub 저장소의 `Settings`를 엽니다.
2. 왼쪽 메뉴에서 `Pages`를 선택합니다.
3. `Build and deployment`를 다음처럼 설정합니다.

```text
Source: Deploy from a branch
Branch: gh-pages
Folder: /(root)
```

4. 설정을 바꿨다면 `Save`를 누릅니다.
5. 잠시 후 `https://yongchanpark.github.io/`를 확인합니다.

배포 반영에는 몇 분이 걸릴 수 있습니다.

---

# 방법 2 — GitHub 웹사이트에서 바로 업로드하기

프로그램을 설치하지 않고 빠르게 적용할 때 사용할 수 있습니다. 이 방법은 예전 파일을 자동으로 삭제하지 않으므로, 저장소가 완전히 깔끔해지지는 않습니다.

## 1단계. 백업

1. 저장소의 브랜치를 `gh-pages`로 선택합니다.
2. `Code` → `Download ZIP`으로 현재 상태를 백업합니다.

## 2단계. 새 파일 업로드

1. `gh-pages` 브랜치의 최상위 화면으로 이동합니다.
2. `Add file` → `Upload files`를 누릅니다.
3. 압축을 푼 패키지 안의 파일과 폴더를 업로드 영역에 끌어다 놓습니다.
4. `Commit message`에 다음처럼 입력합니다.

```text
Redesign academic homepage
```

5. `Commit directly to the gh-pages branch`를 선택합니다.
6. `Commit changes`를 누릅니다.

같은 이름의 파일은 교체되고, 새 파일은 추가됩니다.

## 3단계. `.nojekyll` 확인

업로드 후 저장소 루트의 파일 목록에 아래 파일이 있는지 확인합니다.

```text
.nojekyll
```

운영체제에 따라 점으로 시작하는 숨김 파일이 업로드에서 빠질 수 있습니다.

없다면 다음처럼 만듭니다.

1. `Add file` → `Create new file`
2. 파일 이름에 `.nojekyll` 입력
3. 내용에 아래 한 줄 입력

```text
Static HTML site
```

4. `Commit changes`

`.nojekyll` 파일은 예전 Jekyll 테마 처리를 건너뛰고 정적 HTML 파일을 직접 배포하도록 돕습니다.

## 4단계. Pages 설정 확인

```text
Settings → Pages
Source: Deploy from a branch
Branch: gh-pages
Folder: /(root)
```

## 5단계. 선택 사항: 예전 테마 파일 삭제

사이트가 정상적으로 열린 뒤, 저장소를 정리하려면 다음 예전 파일을 삭제할 수 있습니다.

```text
_config.yml
index.md
_includes/
_layouts/
assets/css/
icons/
```

`resources/`는 삭제하지 마세요.

---

# favicon 사용 방법

이번 패키지에는 `Y` 이니셜을 사용한 둥근 사각형 favicon이 이미 들어 있습니다.

```text
favicon.svg
favicon.ico
favicon-16x16.png
favicon-32x32.png
apple-touch-icon.png
android-chrome-192x192.png
android-chrome-512x512.png
site.webmanifest
```

`index.html`의 `<head>`에 다음 연결 설정도 이미 적용되어 있습니다.

```html
<link rel="icon" href="favicon.svg" type="image/svg+xml">
<link rel="icon" href="favicon-32x32.png" sizes="32x32" type="image/png">
<link rel="icon" href="favicon-16x16.png" sizes="16x16" type="image/png">
<link rel="shortcut icon" href="favicon.ico">
<link rel="apple-touch-icon" href="apple-touch-icon.png" sizes="180x180">
<link rel="manifest" href="site.webmanifest">
```

따라서 파일을 저장소 루트에 함께 올리기만 하면 별도 작업 없이 적용됩니다.

## favicon 색상을 바꾸고 싶을 때

`favicon.svg`를 텍스트 편집기로 열면 다음 색상 값이 있습니다.

```svg
fill="#315a7d"
```

이 값을 원하는 색상 코드로 바꾸면 SVG favicon의 배경색이 바뀝니다.

주의: `favicon.svg`만 바꾸면 PNG와 ICO 파일의 색상은 그대로입니다. 모든 기기에서 같은 색상을 쓰려면 PNG와 ICO도 같은 디자인으로 다시 만들어 교체해야 합니다.

## favicon이 바로 바뀌지 않을 때

favicon은 브라우저 캐시가 오래 남는 편입니다.

- Windows: `Ctrl + F5`
- macOS: `Cmd + Shift + R`
- 시크릿 또는 프라이빗 창에서 확인
- 탭을 완전히 닫았다가 다시 열기
- 몇 분 뒤 다시 확인

---

# 홈페이지 내용 수정 방법

대부분의 내용은 `index.html` 한 파일에서 수정할 수 있습니다.

텍스트 편집기의 검색 기능으로 다음 문구를 찾으면 해당 섹션으로 바로 이동할 수 있습니다.

```text
Yong-chan Park
Research interests
Recent updates
Publications by year
Academic profile and activities
```

## 새 논문 추가

같은 연도의 아래 영역 안에서 기존 논문 블록 하나를 복사합니다.

```html
<div class="publication-items">
  <article class="publication">
    ...
  </article>
</div>
```

제목, 저자, 학회, 링크만 바꾼 뒤 저장하고 다시 커밋·푸시하면 됩니다.

## 새 연도 추가

기존 `publication-group` 전체를 복사하고 연도와 `id`를 함께 바꿉니다.

```html
<section class="publication-group" aria-labelledby="pub-2027">
  <h3 class="publication-year" id="pub-2027">2027</h3>
  ...
</section>
```

---

# 문제가 생겼을 때

## 예전 디자인이 계속 보임

1. 배포 후 몇 분 기다립니다.
2. 강력 새로고침을 합니다.
3. 시크릿 창에서 확인합니다.
4. `Settings → Pages`에서 `gh-pages`와 `/(root)`를 확인합니다.

## 글자만 보이고 디자인이 적용되지 않음

`styles.css`가 `index.html`과 같은 최상위 폴더에 있는지 확인합니다.

## 404가 표시됨

- `index.html`이 저장소 루트에 있는지 확인합니다.
- `yongchan-github-pages-final/index.html`처럼 한 단계 안쪽에 들어가 있지 않은지 확인합니다.
- Pages의 배포 브랜치가 `gh-pages`인지 확인합니다.

## CV 또는 논문 링크가 깨짐

기존 `resources/` 폴더를 삭제했거나 이동했는지 확인합니다.

---

# 원래 사이트로 되돌리기

가장 쉬운 방법은 배포 전에 내려받은 백업 ZIP을 다시 업로드하는 것입니다.

Git을 사용하는 경우에는 새 디자인 적용 직전 커밋으로 되돌릴 수도 있습니다. GitHub Desktop의 `History`에서 이전 커밋을 확인한 뒤 되돌리거나, GitHub 저장소의 커밋 기록에서 이전 상태를 복구할 수 있습니다.

---

# 마지막 점검표

- [ ] `gh-pages` 브랜치에서 작업했다.
- [ ] 기존 저장소를 ZIP으로 백업했다.
- [ ] `resources/` 폴더를 보존했다.
- [ ] 실제 사진을 `assets/profile.jpg`로 교체했다.
- [ ] `index.html`이 저장소 최상위에 있다.
- [ ] `.nojekyll`이 저장소 최상위에 있다.
- [ ] favicon 파일들이 저장소 최상위에 있다.
- [ ] `Settings → Pages`가 `gh-pages`와 `/(root)`로 설정되어 있다.
- [ ] 배포 후 강력 새로고침 또는 시크릿 창으로 확인했다.

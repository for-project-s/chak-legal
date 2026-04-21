# 착(CHAK) Legal Documents

App Store 심사용 법적 문서 — 개인정보 처리방침과 이용약관.

## 파일 구성

```
legal/
├── index.html      # GitHub Pages 랜딩 페이지 (privacy/terms 링크)
├── privacy.md      # 개인정보 처리방침 (Markdown)
├── terms.md        # 이용약관 (Markdown)
└── README.md       # 이 파일
```

## GitHub Pages 셋업 (10분)

### 1. GitHub에서 새 repo 생성
- repo 이름: `chak-legal` (또는 원하는 이름)
- Public으로 설정 (Apple 리뷰어가 접속 가능해야 함)
- README 초기화는 안 함

### 2. 이 폴더 내용을 새 repo에 푸시

```bash
cd /Users/arden/Documents/dev/PS_project/legal
git init
git add .
git commit -m "Initial: privacy policy and terms of service"
git branch -M main
git remote add origin https://github.com/ardenspace/chak-legal.git
git push -u origin main
```

### 3. .md → .html 변환 (선택, 더 예쁜 표시 원할 시)

GitHub Pages는 .md를 자동 렌더링하지만, 더 깔끔하게 보이려면 HTML로 변환 추천:

**옵션 A: 수동 변환 (브라우저 개발자 도구 / 온라인 도구)**
- https://markdowntohtml.com 같은 도구에 markdown 붙여넣고 변환
- `privacy.html`, `terms.html`로 저장

**옵션 B: index.html에서 markdown을 직접 렌더링**
이미 만든 `index.html`은 `.html` 파일을 가리키고 있음. md 그대로 두려면 link 경로를 `./privacy.md`, `./terms.md`로 수정.

> 💡 가장 빠른 방법: GitHub에서 `privacy.md` 클릭하면 GitHub이 자동으로 렌더링한 HTML 페이지가 보임. 그 URL을 그대로 App Store Connect에 넣어도 됨.
> 예: `https://github.com/ardenspace/chak-legal/blob/main/privacy.md`

### 4. GitHub Pages 활성화
1. repo → Settings → Pages
2. Source: `Deploy from a branch`
3. Branch: `main` / `/ (root)` 선택
4. Save 클릭
5. 1-2분 후 URL 발급: `https://ardenspace.github.io/chak-legal/`

### 5. App Store Connect에 입력

App Store Connect → CHAK 앱 → App Information:
- **Privacy Policy URL:** `https://ardenspace.github.io/chak-legal/privacy.html`
  (또는 `https://ardenspace.github.io/chak-legal/privacy.md`)
- **Terms of Service:** 동일 패턴

---

## 문서 수정이 필요할 때

법적 문서는 출시 후에도 변경될 수 있음. 변경 시:
1. `privacy.md` 또는 `terms.md` 수정
2. 시행일자 갱신
3. 앱 내 공지 (변경 시행 7일 전, 불리한 변경은 30일 전)
4. `git commit && git push` → 자동 배포

---

## ⚠️ 출시 전 확인 사항

`privacy.md`와 `terms.md`에서 아래 항목이 실제 운영 환경과 일치하는지 확인:

- [ ] **이메일 주소** — `for.ps.project@gmail.com` (변경 필요 시 두 파일 모두 수정)
- [ ] **사용 중인 외부 API** — 현재 명시: Google OAuth, Google Places, Kakao Local, OpenWeather, Upstage Solar
- [ ] **회원 탈퇴 기능 구현 여부** — 약관에 회원 탈퇴 권리 명시되어 있으므로 앱에 실제 기능 필요
- [ ] **개인정보 열람·수정·삭제 기능** — 최소 이메일 요청 응대 가능 여부 확인

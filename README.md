# 효심노인복지센터 홈페이지

인천 남동구 재가노인요양센터 · 방문요양 안내 사이트.
빌드 도구 없는 정적 HTML 1개 + 이미지 폴더 구조입니다.

```
hyosim-care/
├─ index.html        전체 페이지 (HTML + CSS + JS 한 파일)
├─ .nojekyll         GitHub Pages 처리용 (지우지 마세요)
└─ images/           사진 폴더 — images/README.md 참고
```

---

## GitHub Pages 임시 배포

도메인 구입 전까지 `https://<깃허브아이디>.github.io/hyosim-care/` 로 씁니다.

### 1. 저장소 만들기

github.com → New repository
- Repository name: `hyosim-care`
- **Public** (Private은 Pages 유료 플랜에서만 동작)
- Add a README 체크 해제

### 2. 파일 올리기

```bash
cd hyosim-care
git init
git add -A
git commit -m "효심노인복지센터 홈페이지 초기 배포"
git branch -M main
git remote add origin https://github.com/<깃허브아이디>/hyosim-care.git
git push -u origin main
```

터미널이 번거로우면 저장소 페이지에서 **Add file → Upload files** 로
`index.html`, `.nojekyll`, `images` 폴더를 드래그해도 됩니다.
(`.nojekyll` 은 점으로 시작해 탐색기에서 안 보일 수 있으니 확인하세요.)

### 3. Pages 켜기

저장소 → **Settings → Pages**
- Source: `Deploy from a branch`
- Branch: `main` / `/ (root)` → Save

1~2분 뒤 `https://<깃허브아이디>.github.io/hyosim-care/` 로 접속됩니다.

### 4. 수정 반영

```bash
git add -A && git commit -m "내용 수정" && git push
```

푸시하면 자동 재배포됩니다. 반영이 안 보이면 강력 새로고침(Ctrl+Shift+R).

---

## 도메인 구입 후

1. 저장소 루트에 `CNAME` 파일 생성, 내용은 도메인 한 줄 (예: `hyosim.co.kr`)
2. 도메인 등록업체 DNS에서
   - `A` 레코드 4개 → `185.199.108.153` `185.199.109.153` `185.199.110.153` `185.199.111.153`
   - `www` `CNAME` → `<깃허브아이디>.github.io`
3. Settings → Pages → Custom domain 에 도메인 입력, **Enforce HTTPS** 체크
4. `index.html` 안의 `https://example.com` 을 실제 도메인으로 전부 교체
   (`canonical`, `og:url`, `og:image`, JSON-LD 총 4곳)

---

## 배포 전 남은 작업

- [ ] `hero.jpg`, `about-1~3.jpg` 넣기
- [ ] 장기요양기관 지정번호 (`제0000000000호`)
- [ ] 대표자 성함 (`○○○`), 사업자등록번호 (`000-00-00000`)
- [ ] 이메일 (`hyosim@example.com`)
- [ ] 카카오맵/네이버 지도 '지도 퍼가기' iframe — `오시는 길` 섹션 주석 참고
- [ ] 상담 폼 전송 주소 — `index.html` 하단 `FORM_ENDPOINT`
- [ ] JSON-LD 위경도 (`37.4450 / 126.7310`) 실제 좌표로

## 홍보 순서 참고

홈페이지보다 **네이버 스마트플레이스 등록이 먼저**입니다.
"남동구 방문요양"으로 검색하면 지도 결과가 상단을 차지합니다.
스마트플레이스 프로필에 이 홈페이지 주소를 연결하는 순서가 유입에 유리합니다.

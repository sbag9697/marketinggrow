# 마케팅그로우 웹사이트 배포 가이드

## 📌 1단계: GitHub Pages 배포

### 1-1. GitHub 리포지토리 생성
1. [GitHub](https://github.com) 로그인
2. 우측 상단 **+** 버튼 → **New repository** 클릭
3. Repository name: `marketinggrow` (또는 원하는 이름)
4. Public 선택
5. **Create repository** 클릭

### 1-2. 파일 업로드
1. 생성된 리포지토리에서 **uploading an existing file** 클릭
2. marketing-agency 폴더의 모든 파일 드래그 앤 드롭:
   - index.html
   - styles.css
   - script.js
   - (테스트 파일들은 제외)
3. Commit message: "Initial upload"
4. **Commit changes** 클릭

### 1-3. GitHub Pages 활성화
1. 리포지토리에서 **Settings** 탭 클릭
2. 왼쪽 메뉴에서 **Pages** 클릭
3. Source: **Deploy from a branch** 선택
4. Branch: **main** 선택, **/ (root)** 선택
5. **Save** 클릭
6. 약 5-10분 후 사이트 주소 생성됨:
   - `https://[GitHub사용자명].github.io/[리포지토리명]/`

---

## 📌 2단계: 도메인 구매 및 연결

### 2-1. 도메인 구매처 추천
#### 국내 업체:
- **가비아** (gabia.com) - 가장 대중적
- **카페24** (cafe24.com) - 호스팅 연동 편리
- **후이즈** (whois.co.kr) - 가격 저렴

#### 해외 업체:
- **Namecheap** (namecheap.com) - 저렴, 영문 지원
- **GoDaddy** (godaddy.com) - 글로벌 1위
- **Google Domains** (domains.google) - 구글 서비스 연동

### 2-2. 도메인 구매 절차 (가비아 기준)
1. [가비아](https://www.gabia.com) 접속
2. 도메인 검색: `marketinggrow.com` 또는 `marketinggrow.co.kr`
3. 장바구니 담기 → 구매하기
4. 회원가입/로그인
5. 결제 (연 15,000원~40,000원)

### 2-3. GitHub Pages와 도메인 연결

#### A. GitHub에서 설정:
1. 리포지토리 최상위에 `CNAME` 파일 생성
2. 파일 내용: `marketinggrow.com` (구매한 도메인)
3. Commit

#### B. 도메인 업체에서 DNS 설정:
1. 도메인 관리 → DNS 설정
2. A 레코드 추가:
   ```
   Type: A
   Host: @
   Value: 185.199.108.153

   Type: A
   Host: @
   Value: 185.199.109.153

   Type: A
   Host: @
   Value: 185.199.110.153

   Type: A
   Host: @
   Value: 185.199.111.153
   ```
3. CNAME 레코드 추가:
   ```
   Type: CNAME
   Host: www
   Value: [GitHub사용자명].github.io
   ```
4. 저장 (반영까지 24-48시간 소요 가능)

---

## 📌 3단계: SEO 설정

### 3-1. 네이버 서치어드바이저 등록
1. [네이버 서치어드바이저](https://searchadvisor.naver.com) 접속
2. 로그인 → 웹마스터 도구
3. 사이트 등록: `https://marketinggrow.com`
4. 소유 확인: HTML 태그 방식 선택
5. 제공된 메타태그를 index.html의 `<head>` 부분에 추가
6. 확인 클릭

#### 추가 설정:
- 사이트맵 제출
- 웹페이지 수집 요청
- 로봇 검증

### 3-2. 구글 서치콘솔 등록
1. [구글 서치콘솔](https://search.google.com/search-console) 접속
2. 속성 추가 → URL 접두어 방식
3. URL 입력: `https://marketinggrow.com`
4. 소유권 확인: HTML 태그 방식
5. 메타태그를 index.html에 추가
6. 확인 클릭

#### 추가 설정:
- 사이트맵 제출
- 색인 요청

### 3-3. SEO 메타태그 추가
index.html의 `<head>` 부분에 다음 추가:

```html
<!-- SEO 메타태그 -->
<meta name="description" content="마케팅그로우는 네이버 블로그 체험단, SEO, 소셜미디어 마케팅 전문 에이전시입니다.">
<meta name="keywords" content="네이버 블로그 체험단, 블로그 마케팅, SEO, 소셜미디어 마케팅, 디지털 마케팅">
<meta name="author" content="마케팅그로우">
<meta property="og:title" content="마케팅그로우 | 디지털 마케팅 에이전시">
<meta property="og:description" content="네이버 블로그 체험단 1만원, 방문형/배송형 체험단 서비스">
<meta property="og:image" content="https://marketinggrow.com/og-image.png">
<meta property="og:url" content="https://marketinggrow.com">
<meta name="naver-site-verification" content="네이버에서_제공한_코드">
<meta name="google-site-verification" content="구글에서_제공한_코드">
```

---

## 📋 체크리스트

### GitHub Pages 배포
- [ ] GitHub 계정 생성
- [ ] 리포지토리 생성
- [ ] 파일 업로드
- [ ] GitHub Pages 활성화
- [ ] 사이트 접속 확인

### 도메인 연결
- [ ] 도메인 구매
- [ ] CNAME 파일 생성
- [ ] DNS A 레코드 설정
- [ ] DNS CNAME 레코드 설정
- [ ] 도메인으로 접속 확인

### SEO 설정
- [ ] 네이버 서치어드바이저 등록
- [ ] 구글 서치콘솔 등록
- [ ] 메타태그 추가
- [ ] 사이트맵 생성 및 제출
- [ ] 검색 노출 확인

---

## 💡 추가 팁

### 무료 도메인 옵션
- `.github.io` - GitHub 제공 무료 도메인
- `.netlify.app` - Netlify 제공 무료 도메인
- `.vercel.app` - Vercel 제공 무료 도메인

### 대체 무료 호스팅
1. **Netlify** (추천)
   - 더 쉬운 배포
   - 자동 HTTPS
   - 폼 처리 기능

2. **Vercel**
   - 빠른 속도
   - 자동 배포

### 속도 최적화
1. 이미지 압축
2. CSS/JS 압축
3. CloudFlare CDN 사용

---

## 🆘 문제 해결

### GitHub Pages가 안 보일 때
- Settings → Pages에서 상태 확인
- 10-15분 기다리기
- 브라우저 캐시 삭제 (Ctrl+F5)

### 도메인 연결이 안 될 때
- DNS 전파 대기 (최대 48시간)
- [DNS Checker](https://dnschecker.org) 에서 확인
- CNAME 파일 확인

### SEO 등록이 안 될 때
- 소유권 확인 메타태그 위치 확인
- robots.txt 파일 확인
- 사이트맵 경로 확인
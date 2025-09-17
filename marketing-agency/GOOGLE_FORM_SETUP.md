# 구글 폼 연동 설정 가이드

## 1단계: 구글 폼 만들기

1. [Google Forms](https://forms.google.com)에 접속
2. "빈 양식" 클릭하여 새 폼 생성
3. 다음 필드들을 순서대로 추가:
   - **이름** (단답형)
   - **이메일** (단답형)
   - **연락처** (단답형)
   - **관심 서비스** (객관식 - SEO, 디지털 광고, 소셜미디어, 통합 마케팅)
   - **프로젝트 설명** (장문형)

## 2단계: 폼 ID 및 Entry ID 찾기

### 방법 1: 미리보기 페이지에서 찾기
1. 구글 폼 상단의 "미리보기" (눈 아이콘) 클릭
2. 브라우저에서 개발자 도구 열기 (F12)
3. Elements 탭에서 각 input 필드의 `name` 속성 확인
4. `entry.숫자` 형태의 값이 Entry ID입니다

### 방법 2: 페이지 소스에서 찾기
1. 미리보기 페이지에서 우클릭 → "페이지 소스 보기"
2. Ctrl+F로 "entry." 검색
3. 각 필드의 entry ID 확인

### 폼 ID 찾기
- 구글 폼 편집 화면 URL에서:
  ```
  https://docs.google.com/forms/d/폼ID/edit
  ```
- 또는 미리보기 URL에서:
  ```
  https://docs.google.com/forms/d/e/폼ID/viewform
  ```

## 3단계: HTML 코드 수정

`index.html` 파일에서 다음 부분을 수정:

1. **폼 action URL 수정**
   ```html
   <form id="contactForm" action="https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse" ...>
   ```
   `YOUR_FORM_ID`를 실제 폼 ID로 교체

2. **Entry ID 수정**
   각 input의 name 속성을 실제 entry ID로 교체:
   ```html
   <input type="text" name="entry.1234567890" ...>  <!-- 이름 필드 -->
   <input type="email" name="entry.0987654321" ...>  <!-- 이메일 필드 -->
   <input type="tel" name="entry.1111111111" ...>    <!-- 연락처 필드 -->
   <select name="entry.2222222222" ...>              <!-- 서비스 선택 -->
   <textarea name="entry.3333333333" ...>            <!-- 메시지 -->
   ```

## 4단계: 구글 폼 설정

1. 구글 폼 편집 화면에서 우측 상단 "설정" (톱니바퀴) 클릭
2. **프레젠테이션** 탭에서:
   - "응답 후 메시지 표시" 체크 해제
   - "다른 응답 제출" 링크 표시 체크 해제
3. **응답** 탭에서:
   - 이메일 주소 수집 설정 (선택사항)

## 5단계: 응답 확인

1. 구글 폼 편집 화면에서 "응답" 탭 클릭
2. 제출된 데이터 확인 가능
3. 우측 상단 스프레드시트 아이콘 클릭하여 구글 시트로 연동 가능

## 테스트

1. 웹사이트에서 폼 작성 후 제출
2. 구글 폼 응답 탭에서 데이터 확인
3. 정상적으로 전송되면 완료!

## 주의사항

- CORS 정책으로 인해 직접적인 응답 확인은 불가능
- iframe을 통해 페이지 리로드 방지
- 구글 폼의 스팸 방지 기능이 작동할 수 있음
- 대량 제출 시 reCAPTCHA가 나타날 수 있음

## 대안

더 나은 사용자 경험을 원한다면:
- Google Apps Script 사용
- Formspree, Netlify Forms 등 서드파티 서비스
- 백엔드 서버 구축
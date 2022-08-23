# 📌ai_chameleon
* AI 카멜레온은 사용자가 사진을 업로드하면 세그멘테이션을 통해 사물을 분리하고, 분리된 사물을 각각의 알록달록한 GIF로 만들어주는 웹입니다.
* 셀피를 업로드하여, 세그멘테이션을 통해 뒷배경색을 지정된 컬러 팔레트로 변경하게 됩니다.
* 지정된 여러 개의 색 팔레트 이미지를 모두 출력하여 gif로 생성합니다.
* 생성된 사진은 다운로드하는 것으로 소장할 수 있습니다!

## 1. 제작 기간 & 참여 인원
- 2022.05.18 ~ 2022.05.24
- 팀 프로젝트(4명)

## 2. 사용 기술
>    <img src="https://img.shields.io/badge/Python3-3776AB?style=for-the-badge&logo=Python&logoColor=white">
>    <img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=Flask&logoColor=white">
>    <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=JavaScript&logoColor=white">
>    <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=HTML5&logoColor=white">
>    <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=CSS3&logoColor=white">
>    <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=MongoDB&logoColor=white">

## 3. 아키텍쳐 및 ERD 설계


## 4. 핵심 기능
<details close>
  <summary>📌 로그인/회원가입</summary>
  유효성 검사, 아이디 중복 검사, JWT Token사용, 카카오 소셜 로그인
</details>
<details close>
  <summary>📌 메인페이지</summary>
  - 강아지 히스토리 CRUD<br>
  - 댓글기능<br>
  - 좋아요 기능<br>
  - 팔로우 기능<br>
  - 엘라스틱서치 엔진을 사용한 초성, 해시태그 검색 기능
</details>

<details close>
  <summary>📌 마이페이지</summary>
  - 유저/ 펫 프로필 CRUD<br>
  - 자신의 반려동물 프로필 이미지 등록시 AI로 강아지vs고양이 구분 (fastAPI사용, ec2 분리)<br>
  - DRF페이지네이션<br>
</details>
<details close>
  <summary>📌 산책 매칭 페이지</summary>
  - 매칭 게시판 (CKEditor 사용)<br>
  - 날짜, 지역, 성별, 시간대등 필터 설정으로 검색<br>
  - 실시간 채팅 기능 (Websocket & Django Channels)<br>
</details>

<details close>
  <summary>📌 애견 월드컵</summary>
  - 자신의 반려동물을 자랑하는 이벤트 페이지<br>
  - 이달의 인기 반려동물  (월별 초기화)<br>
</details>

<details close>
  <summary>📌 배포</summary>
  - Docker/EC2사용<br>
</details>

## 5. 핵심 트러블 슈팅
## 6. 

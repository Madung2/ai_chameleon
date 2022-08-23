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

#### 도커 배포 
* 배포 전 과정이 아직 익숙하지 않은 상태에서 도커를 처음 배우고 배포하는게 쉽지 않았습니다.
* 주말을 도커 공부하는 시간으로 배정하고, 따로 [해외 유튜브 튜토리얼 영상](https://www.youtube.com/watch?v=W5Ov0H7E_o4&list=PLOLrQ9Pn6cazCfL7v4CdaykNoWMQymM_C&index=1)을 찾아보면서 도커파일과, 도커컴포즈 파일의 한 문장 한 문장이 무슨 뜻인지 해석하고 [기초부터 잡는 시간](https://velog.io/@tasha_han_1234/%EB%B0%B0%ED%8F%AC1-Dockerfile)을 가졌습니다.
* git hub workflow를 사용해 CI를 진행했고, EC2 인스턴스에 연결된 ubuntu에서 도커컴포즈 파일을 실행했습니다.

#### 실제 서비스 과정중 해킹 시도

* 서비스를 운영해 보면서 구글시트로 피드백을 받았고 [총 38개의 응답을 받을 수 있었습니다.](https://docs.google.com/forms/d/15miCoUt5ddVy4H0caMUbLnNujvHnd3yJsD1HJBhC0co/edit?usp=sharing)
* 피드백을 받는 기간동안 게시물 데이터중 절반이 삭제되고, html태그가 그대로 업로드 되기도 했습니다.
* 정규표현식을 사용해 게시물 업로드시 html 태그가 지워지도록 했습니다.
* views.py에 있는 게시물 업로드 함수등에서 permission_classes를 적용해두지 않은것을 발견하고 오류없이 깔끔하게 적용되도록 할 수 있었습니다. 
* 그 외에도 피드백 내용을 자세히 읽고 상당부분을 적용해 유저 친화성을 높였습니다.

#### 쿼리 최적화 문제와 리팩토링
* 피드백을 받는 과정에서 쿼리를 많이 날린다는 말을 들었고 쿼리 최적화에 신경을 많이 썼습니다.
*  기존 코드 :
![code44](https://user-images.githubusercontent.com/104334219/186108766-539d5114-9c39-4746-9b26-b22833330c54.png)
*  리팩토링된 코드 :
![code55](https://user-images.githubusercontent.com/104334219/186109137-99a328cd-cbc5-4e4f-888a-244600b4e1bd.png)
*  쿼리디버거를 사용해 쿼리의 갯수와 시간을 체크해보는 과정도 거쳤습니다.
![code3333](https://user-images.githubusercontent.com/104334219/186109296-fda11b91-0b4d-497c-9388-494888f008c9.png)
![image](https://user-images.githubusercontent.com/104334219/186157032-908983d1-16a8-48db-a3f9-c96bb1efb87e.png)


## 6. 기타 트러블 슈팅
<details close>
  <summary>📌EC2배포 초반 sqlite에서 postgreSQL로 바꾸면서 속도가 오히려 줄어든 문제 </summary>
	<br>
  EC2 배포를 처음 시작하면서 로컬에서 했을 때에 비해 속도가 확연하게 줄어든걸 느낄 수 있었습니다.<br>
  개발자도구->Network->fetch 탭에서 확인해봐도 눈에 띄는 속도차이가 드러났습니다.<br>
  이건 내 지식으로 해결하기 어려운 부분이다 싶어서 튜터님들과 잘 아시만한 분들을 찾아갔고,<br>
  EC2 배포할때 지역이 한국이 아닌 캘리포니아로 설정되어 있었단걸 발견습니다.<br>
  그 외에도 당시 EC2서버는 내가 배포하고 postgreSQL을 배포한 RDS서버는 다른 팀원이 배포했는데 이게 문제가 될 수 있다는 얘기를 들어,
  RDS도 내가 배포하게 되었습니다. 
</details>
<details close>
  <summary>📌drf pagination이 settings.py에서 전역설정으로 되지 않는 문제 </summary>
	<br>
  자동 drf 페이지네이션 기능 일반적인 apiview가 아닌 viewsets이나 generic views 사용 할 때만 가능합니다.<br>
  pagination.py파일을 만든뒤 mixin을 사용해서 페이지네이션 api 자체를 불러왔습니다.<br>
	<img src='https://user-images.githubusercontent.com/104334219/186115201-e6669f4f-8aec-44f6-8dd2-caf038b320ed.png'>

</details>
<details close>
  <summary>📌마감 기능 백엔드로 처리시 어려움</summary>
	<br>
  프로젝트 초기에 친구매칭 프로그램의 마감기능을 프론트에서 자바스크립트로 처리했었는데, 이를 리팩토링하는 과정에서 백엔드로 옮겨왔습니다.<br>
  메소드를 마치 필드인 것처럼 취급할 수 있게 해주는 property decorator를 사용해서 생각보다 간단하게 해결할 수 있었습니다. <br>
<img src='https://user-images.githubusercontent.com/104334219/186092270-471d1c5e-5ee4-460d-bf7a-49af8a72242e.png'>
</details>
<details close>
  <summary>📌팀 협업 문제</summary>
	<br>
  팀 활동 초기에 팀 분위기가 다운되어 있었고, 다들 활동시간이 달라 업무 관련 커뮤니케이션이 잘 되지 않는 문제가 있었습니다.<br>
  매일 점심식사 전에 회의를 하기로 정한 뒤, 시간이 되면 팀원들을 전화해서 불러들이고 회의를 주도해나갔습니다.<br>
  이후 회의 문화와 모르는 것이 있으면 바로 팀원에게 질문하는 문화가 정착이 되었고,<br> 커뮤니케이션이 가장 잘 된 팀중에 하나였다고 생각합니다.<br>
  덕분에 혼자서 하기 어려운 기능들도 함께 도전해보고 성취해낼 수 있었습니다.<br>
</details>



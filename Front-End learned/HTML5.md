### HTML 



- 요소 element =  HTML 페이지를 구성하는 각 부품 

- 태그 tag =  이러한 요소를 만들 때 사용하는 작성 방법 

- 속성 attribute 



#### 내용을 가질 수 있는 요소 

- `<h1> Hello HTML5 </h1>`  

- `<p>즐거운 웹 프로그래밍 입문 </p>`

- `<audio></audio>`



#### 내용을 가질 수 없는 요소 

- `</h1>`



- 뒤에 무조건 </> 가 붙어야 함 



#### 줄 바꿈 

- `<br>`  

- `<link href="my.css" rel="stylesheet">` link 에는 두개의 속성이 필수적 (외부 스타일 시트)



#### 경고창 

- `<script>
  	alert("^^"); 
  </script>`



<script src="my.js"> 


#### 오류 수정은 

- F12 누르고 새로고침 



#### 밑줄은

-  `<hr>`



#### 글자 간격 넓히고 싶을때 

- `&nbsp;` 

- `<h2>i&nbsp;&nbsp;&nbsp;&nbsp;     ndex</h2>`



#### 꺽새 

- `&lt;`  `&gt;`  < >

- `<h3>&lt;index&gt;</h3>`



#### & 표시 

- `&amp;`  



<br>`<a href="#jes">이 페이지의 마지막 문단으로 가기</a>`

href="#갈 위치"

`<p id="jes">`





### 목록 태그 



#### 셀 합치기 

rowspan="?"

물음표에는 합치고자 하는 셀의 수 만큼 숫자로 쓰기 1,2,3~

그리고 아래 같은 내용의 내용은 삭제 

`</td><td rowspan="3">영어`



### 미디어 태그 



#### 이미지 넣는 법 

- `img src='game.jpg' alt="게임" width="300"`



#### 사진을 안보이고 설명만 넣고 싶을때 이렇게 작성하면 

#### 사진은 안나오고 설명만 나온다 

- `alt="게임 사진"`





### 음악 삽입 

삽입하고자 하는 오디오 파일을 HTML과 같은 페이지 폴더에 복사 후 붙여넣기 

그 다음 해당 파일을 더블클릭 하면 소스가 나타남 

<body>

`<audio controls="controls">
    <source src="Kalimba.mp3" type="audio/mp3">
    <source src="Kalimba.ogg" type="audio/ogg">
</audio>`



### 동영상 삽입

`<video controls="controls">
    <source src="Wildlife.mp4" type="video/mp4">
    <source src="Wildlife.webm" type="video/webm">
</audio>`



### 동영상을 불러오는 동안 보여주는 이미지 실행법 



`<video controls="controls" `poster="http://placehold.it/640X360"`>
    <source src="Wildlife.mp4" type="video/mp4">
    <source src="Wildlife.webm" type="video/webm">
</audio>`



poster="http://placehold.it/640X360

위를 삽입 



### 파일 확장자 

| 음악 | 비디오 |
| :--: | :----: |
| MP3  |  MP4   |
| OGG  |  WebM  |
| WAV  |  OGV   |



### 입력 양식 



<body>

`<form action="servlet_name" method="get">
	<input type="hidden" name="sign" value="memberInsert" >
	name <input name="name"> <br>
	id <input name="id"> <br>
	pw <input type="password" name="pw"> <br>
	사진 <input type="file" name="file"> <br>
	분야 java <input type="checkbox" name="language" value="java"> 
		c <input type="checkbox" name="language" value="c">
		python <input type="checkbox" name="language" value="python"><br>`


		성별 여<input type="radio" name="gender" value="여"> 
		    남<input type="radio" name="gender" value="남"> <br>
	<input type="submit" value="회원가입">
	<input type="button" value="경고" onclick="alert('잘되나요?')">
	<input type="reset" value="reset">
	<input type="image" src="game.png" width="300" name="img">
  </form>
</body>




















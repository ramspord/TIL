### 공공(오픈)데이터 API 사용법

1. API  (Application Programming Interface)

   통신 규약

   

2. JSON (JavaScript Object Notation)

   서버와 웹페이지간에 어떤 데이터를 주고 받을 때 많이 사용하는 포맷 형식이다.

   데이터 저장 방식 

   객체 상태로 데이터를 전달할 수는 없기에 객체를 문자열로 변환해서 전달해줘야 한다. 

   받은 쪽에서는 다시 문자열을 객체로 변환해야지만 해당 프로그래밍 언어에서 객체로써 사용할 수 있다.

   

   JSON은 "속성: 값" 또는 "key:value"의 쌍으로 이루어진 데이터 객체를 전달하기 위해 만들어진 포맷.

   쌍따옴표를 사용해서 속성 값을 묶음 

   

   사람이 읽기에(보기에) 좋은 구조와 텍스트를 사용. 

   웹상에서의 비동기 처리 기반의 브라우저/서버 통신 등에서 데이터를 주고 받을 때 많이 사용.

   기존의 XML보다 훨씬 더 가볍고, 간결하고 쉽다. 

   거의 모든 언어를 지원.

   계층적인 구조를 가지고 있다. = XML도 마찬가지 

   

   #### JSON 객체

   1. 객체 

   - JSON 객체 -- 중괄호 사용 {}
   - JSON 에서 객체란 -- key:value의 한 쌍으로 이루어진 정렬되지 않은 속성(property)들의 집합. 
   - ,(콤마)로 구분하여 여러개의 속성을 가질 수 있다. 
   - 문자열은 반드시 큰따옴표("")로 묶어준다. 
   - 문자열이 아닌 숫자는 따옴표 없이 써도 된다. 

   

   {

   ​	"name" : "홍길동",

   ​	"age" : 20,

   ​	"nationality" : "대한민국"

   }

   

   2. 객체안의 객체 (계층적 구조)

   {

   ​	"name" : "홍길동",

   ​	"age" : 20,

   ​	"nationality" : "대한민국",

   ​	"company" : {

   ​		"cname": "원자력 발전소",

   ​		"cphone" : "02-1234-5678",

   ​		"caddress" : "경기도 부천시 다당다당"

   ​		}

   }

   

   3. JSON 배열  -- 대괄호 [] 사용 

      "person" : [

      ​	{"name" : "홍길동","age" : 20, "nationality":"한국"}.

      ​	{"name" : "데이빗","age" : 30, "nationality":"미국"},

      ​	{"name" : "사쿠라","age" : 40, "nationality":"일본"}

      ]



#### JSON 데이터를 다루기 위한 JS 기본 사용법

[1]

const person = [

​	{"name" : "홍길동","age" : 20, "nationality":"한국"},

​	{"name" : "데이빗","age" : 30, "nationality":"미국"},

​	{"name" : "사쿠라","age" : 40, "nationality":"일본"},

​	{"name" : "뿌빠뽕","age" : 50, "nationality":"태국"}

];



console.log (typeof person); //object

'  ' 를 붙히면 String으로 나온다 (개발자도구에서)



[2] 출력 

console.log (person[0].name + "" + person[0].age + "" + person[0].nationality);



[3] 반복 

console.log (...person); //전개 연산자 (모든 요소들이 다 출력된다)

console.log ([...person] [0].name); //홍길동 (특정 요소만 추출하고 싶을때)

console.log ([...person].length); //4  (객체가 몇개인지)



[4] 반복 가능한 객체 

###### for...of

for (let ele of person) {       // person -- iterable 반복 가능한 객체만 와야 함. 값이 출력됨

​	console.log(ele); 

}



###### for...in 

for (let i in person) {       // 배열 0 1 2 3

​	console.log(i); 

}



for (let k in person) {       // name,age,nationality  key 값이 출력됨

​	console.log(k); 

}



[5] 수정

person[0].name = "홍길자";

person[0].age = 22;

console.log

```json
(` 홍길동의 이름이 ${person[0].name}로 수정되었고, 나이는 ${person[0].age}살로 수정되었습니다. `);
```

역따옴표로 감싸면 됨 위 문장을 



### 중첩된 JSON 데이터 다루기 

const book = {

​	"isbn":"123-456-789",

​	"author":{

​		"name":"홍길동"

​		"email":"hong@gmail.com"

​	},

"editor":{

​		"name":"이순재"

​		"email":"lee@gmail.com"

​	},

"title":"대한민국의 정의는 죽었는가?",

"category":[

​	"Non-Fiction","IT","politics"

​	]

}



console.log(book["author"].name); //홍길동

console.log(book["editor"].name);  //이순신



console.log(book.isbn);   //123-456-789

console.log(book.title);     //.연산자 방식

=

console.log(book["title"]); 



#### 개별 엑세스 

let val = " ";

val =book.category[0];

document.getElementById("aaa").innerText=val;



//반복문을 이용한 엑세스 

//for 

```json
for (let i=0; i<book.category.lenth; i++){

	val +=book.category[i] + "<br>";

}
document.getElementById("aaa").innerHTML=val;
```



```
for..in 
for(let i in book.category){
	val +=book.category[i] + "<br>";
}

//
for..of
for(let value of book.category){
	val+=value+"<br>";
}
document.getElementById("aaa").innerHTML=val;
```



#### JSON 데이터 객체와 문자열로 변환하기

JSON.parse()  객체로 변환 

JSON.stringify() 문자열로 변환 



[1] : JSON.parse(jsonText) -- JSON 형식의 텍스트를 자바스크립트 객체로 변환 



```
let jsonText = `{"name" : "홍길동","age" : 20, "nationality":"한국"}`;
따옴표가 들어가 있으면 텍스트 
```

console.log ( typeof jsonText); //string



```
let jsonText = {"name" : "홍길동","age" : 20, "nationality":"한국"};
따옴표가 빠지면 객체 
```

console.log(jsonText.name); //object



const jsonObj = ISON.parse(jsonText);

jsonText가 JSON.parse 메서드를 통해 jsonObj 객체로 변환되는 과정 

console.log(jsonObj.name + " " +jsonObj.age + " " +jsonObj.nationality);  //



const jsonStr=JSON.stringify(jsonObj);

console.log(jsonStr);



#### JSON 데이터를 웹페이지로 출력하기 

Parsing -- 다른 형식으로 저장된 데이터를 목적에 맞는 형태의 형식으로 변환하는 것 

JSON Parsing -- JSON 형식의 텍스트 문자열을 목적에 맞게 객체로 변환. 
































### JavaScript



식별자 뒤에 괄호 없음 - 변수 - 속성 

식별자 뒤에 괄호 있음 -  함수 - 메서드 



<script type="text/javascript">
		var age=20;
		var name="홍길동";
		var height=160.5;
		var isPretty=false;
		var birthday=null;

		window.alert();

</script>



값이 상수이면 const

값이 변수이면 let 



JavaScript에는 값을 포함할 수 있는 5가지 다른 데이터 유형이 있습니다.

- `string`
- `number`
- `boolean`
- `object`
- `function`

6가지 유형의 객체가 있습니다.

- `Object`
- `Date`
- `Array`
- `String`
- `Number`
- `Boolean`

값을 포함할 수 없는 2가지 데이터 유형:

- `null`
- `undefined`



#### 자바스크립트 콜백

callback 

매우중요 





<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<script type="text/javascript">

​	
​		
		window.onload=function(){
			let obj=document.querySelector("img");
			obj.src="hanbit.jpg";
			obj.width=300;


​			
​			
​			
			setInterval(function (){
				let div=document.querySelector("div");
				let today=new Date();
				div.textContent=today;
			}, 1000);
			
			}


</script>
</head>
<body>
		<img>
		<div></div>
</body>
</html>


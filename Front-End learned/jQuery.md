### jQuery





CDN



$  = jquery 

() = 생성자 

안쪽에 document 

. 점 찍고 

 ready();

안쪽에 

function(){}

넣고 

{} 중괄호 펼쳐서 안쪽에 내용 넣기 



$(document).ready(function(){

alert();

});



css 스타일을 제어

attr  속성을 제어 



  <script type="text/javascript">
	$(document).ready(function(){
		$("#who_a").click(function(){
			alert("^^");

		});
		
	});  

  </script>

 <li><a href="#" id="who_a">WHO</a></li>







<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>

	<style type="text/css">
	#box {
			width: 100px;
			height: 100px;
			background:blue;
	}
	
			#box:hover{
			background:yellow;
			border-radius:50px;
	}
	
	</style>
	<script src="https://code.jquery.com/jquery-3.6.0.js" integrity="sha256-H+K7U5CnXl1h5ywQfKtSj8PCmoN9aaq30gDh27Xc0jk=" crossorigin="anonymous"></script>
	
	<script type="text/javascript">
	
		$(document).ready(function(){
			$("button").css("background","red");
			
			let obj={src:"hanbit.jpg", width:100};
			
			//$("img").attr("src","hanbit.jpg");
			//$("img").attr("width","300")
			
			$("img").attr(obj);
			let a=$("img").attr("width");
			console.log(a);
			
			$("#header").text("Header");
			$("#footer").html("<a href='#'>Footer</a>");// 중요
			
			$("#header").click(function(){ //중요 이벤트 
				let a=$("#header").text();
				alert(a);
				//alert($("input").val());


​				
			});
			
			$("button").click(function(){ //이벤트처리 
				$("input").val("황세철");
				//let a=$("input").val();
				
			});


​			
​			
		});
	
	</script>


</head>
<body>
		<h1 id="header"></h1>
​		<input>
​		<button>전송</button><br>
​		<img>
		<h1 id="footer"></h1>
		<div id="box"></div>
</body>
</html>
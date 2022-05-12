BufferedReader 버퍼를 이용해서 읽고 쓰는 함수 

입출력 속도 향상을 위해서 데이터를 일시적으로 메모리 영역의 한 곳에 모아두는 것. 

버퍼를 이용하기 때문에 입출력 관련 처리작업을 매우 빠르게 할 수 있다. 



변수에 여러 값을 넣어서 주소 체계를 만들어야 한다면 

StringBuilder를 사용 /대부분의 공공 API가 StringBuilder 방식을 사용함 

StringBuilder는 문자열을 더해 나갈 때 새로운 객체를 매번 생성하는 것이 아니라 기존 데이터 값에 추가해가는 방식으로 속도가 빠른 장점이 있음. 

mutable 속성이고 append(), insert(), delete()등을 사용해서 값을 변경. 





ctrl + shift + o  자동 임포트 단축키 



```
BufferedReader br = null;
try {

String urlStr = API  주소

//URL 클래스로 객체 생성 
URL url = new URL (urlStr);

//openConnenction() 메서드를 이용한 연결 
//URL 주소의 원격 객체에 접속한 뒤 통신할 수 있는 URLConnection 객체 리턴.
HttpURLConnection urlConn = (HttpURLConnection) url.openConnection(); 
urlConn.setRequestMethod("GET"); //대문자 필수 
urlConn.setRequestProperty("Content-type","application/json"); //key:value
System.out.print("Response code:"+urlConn.getResponseCode()); //200

//200이 와야 잘 전달받았다는 뜻 그게 아니면 404가 뜬다. 

//InputStreamReader 클래스로 읽기 
//BufferedReader는 InputStreamReader의 객체를 입력값으로 사용.
br = new BufferedReader(new InputStreamReader(urlConn.getInputStream(),"UTF-8"));

//결과변수
String rst = "";
String line;
while ( (line =  br.readline())!=null) {
 rst +=line + "Wn";
}
System.out.println(rst);

//다른 예시 값은 동일함 
StringBuilder sb= new StringBuilder();
String line;
while((line = br.readLine())!=null) {
	sb.append(line);
}
System.out.println(sb.toString());

//연결해제
br.close();
urlConn.disconnect();


}
catch(Exception e) {
 System.out.println(e.getMessage());
 
	}
}



```


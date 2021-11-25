세미 프로젝트 웹 사이트 만드는 법 



static 정적인 정보가 들어가는 곳 

웹 템플릿 집어넣는 곳 css등 



`<span id="loginDiv">ID<input id="id" size="2"> PW<input id="pw" type="password" size="2"><button id="loginBtn">login</button></span>`

로그인 버튼 만드는 코드 



<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="js/my.js"></script>



메인 자바에 

데모 컨트롤러 클래스를 만들어서 

@Controller
public class MemberController {

	@ResponseBody
	@RequestMapping("login")
	public String login(HttpServletRequest request, HttpServletResponse response) {
		String id=request.getParameter("id");
		String pw=request.getParameter("pw");
		System.out.println(id+":"+pw);
		return id+"님 login ok";

이렇게  작성한 뒤 로그인하면 콘솔에 정보가 뜬다 



$(document).ready(function(){
	$("#loginBtn").click(function(){
		const id=$("#id").val();
		const pw=$("#pw").val();
		alert(id+":"+pw);
		$.post('login',{id,pw},function(data){
			console.log(data);	
			

		});
		
	});
});



여기가 먼저 로그인 과정 



contact us 활성화 방법 

public - index.html 

들어가서 contact us   찾은 다음 

window.open("https://www.w3schools.com", "_blank", "toolbar=yes,scrollbars=yes,resizable=yes,top=500,left=500,width=400,height=400");

onclick=' '  싱글쿼테이션 안에 위 링크를 붙여넣기 한 후 

주소에 memberInsert.html 를 넣으면 해당 주소가 출력된다 



그리고 거기에 로그인 출력화면을 만든다 

memberInsert_pretty 집어넣고 

controller / VO 클래스 말고 정보 집어넣기 

@Controller
public class MemberController {

	@RequestMapping("memberInsert")
	@ResponseBody
	public String memberInsert(@ModelAttribute("memberVO")MemberVO memberVO) {
		System.out.println(memberVO);
		return "memberInsert ok";
	}
}



이렇게 컨트롤러 작성하고 vo 생성 

그리고 vo에 생성자 투스트링 등등 

public MemberVO(String loginId, String loginPw, String loginPwConfirm, String name, String email, String nickname,
			String cellphoneNo) {
		   ``setLoginId(loginId);
		setLoginPw(loginPw);
		setLoginPwConfirm(loginPwConfirm);
		setName(name);
		setEmail(email);
		setNickname(nickname);
		setCellphoneNo(cellphoneNo);``
		

	}

위 처럼 vo 파일  이름 바꾸기 



application properties

spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp



외우기 







파일 생성

application properties  코드 입력 

wep app =web INF = views 파일 생성 



pom.xml  - jsp를 위한 라이브러리 생성 

dependency  코드 입력 




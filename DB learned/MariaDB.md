## MariaDB 작성법 



모든 코드는 쿼리 에서 작성 



CREATE TABLE member(   // 테이블 생성법
 id VARCHAR(10),
 NAME VARCHAR(20),
 addr VARCHAR(50)   //여기까지는 열 생성 
 );

 

INSERT INTO member(id, NAME, addr) VALUES('1', '전은수', '부천');
INSERT INTO member(NAME, id, addr) VALUES('홍길동', '2', '서울');
INSERT INTO member(addr, NAME, id) VALUES('제주', '이효리', '3');  //여기는 열에 정보 입력 

SELECT * FROM member;  //여기는 전체 출력 





여러줄 주석은 

/*  */

한줄 주석은 

샵 하나랑 내용 샵  (샵 = #)



고객 이름   <- 처럼  

한 칸 띄우고 출력해야 할때는 

양 끝에 떠블 코테이션 ( "   ") 붙여주기 

"고객 이름"








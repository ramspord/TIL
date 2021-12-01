### Docker 

image 도면 

container 건물 



MobaXterm 이란 원격 접속 툴 



원격 접속 툴을 이용해 linux OS를 컨트롤 ubuntu 



Docker

AWS 



AWS 에서 EC2  인스턴스 생성 

t2.micro 

30G

pem key

등등 



이후 MobaXterm 

Session 클릭 후 

퍼블릭 IPv4 주소 복사 붙여넣기  이름은 ubuntu 이후 

폴더열기로 key 열고 사용 시작 





#### ubuntu 에 docker 설치 

- sudo apt update (기존 버전이 오래된 버전일수 있기에 update를 통해 최신버전으로 업데이트)
- sudo apt install docker.io (최신버전으로 업데이트 후 도커를 설치)
- docker -v (도커 상태 확인)



#### 도커에 mysql 5.7 설치 및 가동법

- sudo docker run -d -p 3306:3306 -e MYSQL_ALLOW_EMPTY_PASSWORD=true --name mysql mysql:5.7 

  (run은 image 파일을 컨테이너로 만드는등 모든 절차 시작 명령어, -d 는 백그라운드에서만 운행시키는 명령어, -p는 3306의 포트를 사용하겠다는 의미 // 뒤에 name 앞에는 -- 대쉬가 두 개임 // 첫번째 mysql 앞에 HSC_mysql 와 같이 별명을 지정할 수 있음)

- docker exec -it mysql /bin/bash 

  (bash는 리눅스에서의 명령 프롬프트명 exec  -it 는 거기로 진입하겠다는 뜻 

  역시 mysql 앞에 별명 붙일 수 있음 )

- mysql -uroot (mysql 클라이언트 실행하기)

- show databases; (mysql 명령해보기)

- quit; (mysql client 빠져나오기)

- exit (mysql이 돌고 있는 컨테이너(Debian 9)빠져 나오기)



#### 이외 도커 명령어 

- cat /etc/issue (현재 머신 확인하기)

- sudo docker ps (도커에 현재 동작하고 있는 컨테이너 확인해보기)

- sudo docker exec -it mysql mysql -uroot (도커 mysql client로 바로 들어가보기)

  

#### mysql 에 새 db 와 테이블 만들어보기 

- create database test; (test는 DB 이름)
- use test; 
- create table member( no int primary key auto_increment, name varchar(30), id varchar(10), pw varchar(10));
- show tables; (table 보기)
- desc member; (table 세부정도 int, varchar 등등)
-  insert into member(name,id,pw) values('jes','secure','block');
- select * from member;
- quit;



#### mysql 컨테이너를 종료했다 다시 올려보기

- sudo docker ps (불 켜져있는지 확인하기)
- sudo docker stop mysql
- sudo docker ps (잘 꺼졌는지 확인하기)
- sudo docker start mysql
- sudo docker ps
- sudo docker exec –it mysql mysql –uroot 
-  show databases; (이전에 했던 작업이 저장되어 있는 것을 확인한다)
- quit;



#### mysql 컨테이너 이미지를 삭제했다 다시 올려보기

- sudo docker ps
- sudo docker stop mysql
- sudo docker ps
- sudo docker rm –f mysql (rm은 remove 삭제하다  -force 은 강제하다라는 뜻 )
- sudo docker start mysql (에러 남)
- sudo docker images
- sudo docker rmi –f   IMAGE ID  (이미지 아이디는 8b43c#!d 처럼 되어있는 아이디 더블클릭 후 마우스 오른쪽키를 누르면 자동으로 붙여넣기가 된다.)
- sudo docker images
- sudo docker run -d -p 3306:3306    	-e MYSQL_ALLOW_EMPTY_PASSWORD=true --name mysql mysql:5.7
- sudo docker exec –it mysql mysql –uroot
- show databases; (다시 받았으므로 test DB와 member 테이블은 없다) 



vi 는 메모장 작성할땐 이런 식  `vi index.html`  

수정하고자 할 땐  i  

메모장에 html 코드 입력 

esc 누르면서 :  누르면 공간이 생긴다  거기에 wq! 엔터 누르면 빠져 나온다 

nginx  는 톰캣과 같은 웹 서버 

cd 는 경로 지정 

../../  두번 위로 지정 

방향키 위로 를 누르면 이전에 쳤던 명령어들이 역순으로 나온다 

Ctrl+P Ctrl+Q  우분투로 빠져나오기 



####  도커 레지스트리에서 tomcat 8 이미지 받아 웹어플리케이션 추가해보기

- Cloud>ubuntu18> sudo docker pull tomcat:8.0 (톰캣 받아오기 )

- Cloud>ubuntu18> sudo docker images

- Cloud>ubuntu18> sudo docker run –d –-name tomcat8 –p 8080:8080 tomcat:8.0

- Cloud>ubuntu18> sudo docker psCloud>ubuntu18> 웹브라우저로[ http://localhost:8080](http://localhost:8080/) 로 확인 

- Cloud>ubuntu18> mkdir 0jes/git_registry

- Cloud>ubuntu18> cd 0jes/git_registry

- Cloud>ubuntu18> git clone https://github.com/javanism/down (깃허브에서 down 폴더 내려받기)

- Cloud>ubuntu18> cd down (다운 폴더로 이동)

- Cloud>ubuntu18> sudo apt-get install unzip 

  (zip을 풀기 위해선 unzip이란 압축풀기 프로그램을 설치해야한다)

- Cloud>ubuntu18> mkdir openeg | unzip openeg.war –d openeg/  

  (두 가지 일을 동시에 하는 것을 파이프라인이라고 부르는데/ openeg라는 폴더를 만드는 동시에 .war를 openeg에 푸는 것이다.)

- Cloud>ubuntu18> sudo docker cp openeg tomcat8:/usr/local/tomcat/webapps/ 

  (openeg폴더를 tomcat8이라는 이름을 가진 컨테이너의 /usr/local/tomcat/webapps 밑으로 복사하라는 것)

- Cloud>ubuntu18> sudo docker exec –it tomcat8 /bin/bash

- Cloud>ubuntu18>docker>Devian9> cd webapps

- Cloud>ubuntu18>docker>Devian9> ls (openeg가 복사되었는지 확인)

- Cloud>ubuntu18> 웹브라우저로[ http://localhost:8080](http://localhost:8080/)/openeg 로 확인 (index 화면은 잘보임)



#### mysql를 설치하면서 볼륨 설정하는 법 



sudo docker run -d -p 3306:3306    	

-v ~/0jes/mysql_data:/var/lib/mysql    	-e MYSQL_ALLOW_EMPTY_PASSWORD=true --name mysql mysql:5.7



#### EC2 타임존 변경법  



date

sudo rm /etc/localtime

sudo ln –s /usr/share/zoneinfo/Asia/Seoul   /etc/localtime

date



### 도커 타임존 변경법 

도커 설치하자마자 해야 됨 

sudo docker run -p 8090:8090 -v /etc/localtime:/etc/localtime:ro -e TZ=Asia/Seoul bummy



### 서비스 배포법 



1. AWS 에서 인스턴스를 생성한다

2. 연결할 포트를 지정하고 시작 

   8080 위치 무관/8090 위치 무관 등 



- sudo apt update 

- sudo apt install docker.io 

- docker -v 

  

- mkdir 0jes

- mkdir 0jes/mysql_data 

  

- sudo docker run -d -p 3306:3306 -v ~/0jes/mysql_data:/var/lib/mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=true --name kim_mysql mysql:5.7 

- sudo docker ps

  

-  sudo docker run -d --name tom_tomcat -p 8080:8080 -v ~/0           jes/tomcat_data/openeg:/usr/local/tomcat/webapps/openeg javanism/openeg:1

- cd 0jes/git_registry  (없으면 모바엑스텀 메뉴 0jes 들어가서 만든다)

- git clone https://github.com/ID/down (나중에 서비스를 만들고 war파일로 압축해서 깃헙에 올리면 이런식으로 aws에 받아온다)

- ls (down 폴더 있는지 확인)

- cd down 

- ls 

- sudo apt-get install unzip  (압축해제를 하기 위해선 압축해제 프로그램을 다운받아야함)

- unzip openeg.war -d ~/0jes/tomcat_data/openeg/ 

- cd ~  (홈으로 나오기)

- cp ~/0jes/git_registry/down/openeg_DDL.sql ~/0jes/mysql_data/ (깃헙에서 받아온 파일을 mysql_data파일로 복사하는 작업)

- cd 0jes

- cd mysql_data 

- cat openeg_DDL.sql  (확인)

- sudo docker ps 

- sudo docker exec -it kim_mysql bash 

- pwd

- ls

- cd /var/lib/mysql 

- ls 

- mysql -uroot 

- show databases; 

- create database openeg;  (DB와 연동할 DB테이블명(메뉴명))

- use openeg; 

- show tables; (잘 옮겨왔는지 확인)

- source openeg_DDL.sql  (source 뜻 ? )

- show tables; 

- create user admin@'%' identified by 'apm/setup'; (기호 뜻? )

- grant all privileges on openeg.* to admin@'%' identified by 'apm/setup';  (/보안용)

- quit;

- exit 

- cd ~

- cd 0jes/tomcat_data/openeg/WEB-INF/classes/config/ 

- ls 

- vi dbconn.properties  (안쪽 정보 수정 IP와 ID 비번)

- cd ~

- sudo docker stop tom_tomcat  (홈페이지가 잘 안뜬다면  웹서버 껏다 다시 켜주기)

- sudo docker start tom_tomcat 






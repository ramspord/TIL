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

  (bash는 리눅스에서의 명령 프롬프트명  -it 는 거기로 진입하겠다는 뜻 역시 mysql 앞에 별명 붙일 수 있음 )

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










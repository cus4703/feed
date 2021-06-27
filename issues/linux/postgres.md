# :newspaper: linux Centos 7 Postgresql 12 설치하기

## 설치 환경에서 외부망이 접속이 안될 경우
### 설치 파일 다운로드 필요!!
### [Linux Postgres 설치파일](https://github.com/ungseokchoi/feed/blob/master/issues/file/postgres) :point_left:

### 기본 install 방법
#### yum 을 통한 install
- Repository 업데이트   
  rpm -Uvh https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm    
  
- postgresql 12 설치  
  yum -y install postgresql12-server postgresql12-contrib   
  
#### file 을 통한 install    
- 순서대로 명령어를 실행  
  sudo rpm -ivh /파일경로/postgres1.rpm   
  sudo rpm -ivh /파일경로/postgres2.rpm   
  sudo rpm -ivh /파일경로/postgres3.rpm   
  sudo rpm -ivh /파일경로/postgres4.rpm
  
### 기본 데이터 베이스 생성
- 설치 후 따로 경로를 변경할 경우 경로 수정과 기타 설정값을 추가로 변경해줘야한다. :star:     
  sudo /usr/pgsql-12/bin/postgresql-12-setup initdb
  
### service 등록 과 데이터베이스 서비스 실행
- 설치시 기본적인 service 가 같이 설치된다. 그러므로 추가적인 service 파일을 만들지 않아도 됨.  
  sudo systemctl enable postgresql-12   -- 서비스 등록
  sudo systemctl start postgresql-12    -- 서비스 실행
  
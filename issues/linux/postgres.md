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
  
### 데이터 베이스 접근 권한 설정
- pg_hba.conf 파일 관련 설명
``` text
# TYPE  DATABASE        USER            ADDRESS                 METHOD
# IPv4 local connections:
host    all             all             127.0.0.1/32            md5
# IPv6 local connections:
host    all             all             ::1/128                 md5
# Allow replication connections from localhost, by a user with the
# replication privilege.
#host    replication     enterprisedb        127.0.0.1/32            md5
#host    replication     enterprisedb        ::1/128                 md5
local   all   all   md5
```
* Authentication Method     
    이 부분은 실제적인 계정의 패스워드에 대한 서버로의 전송을 어떻게 할 것인가를 정하는 것입니다.          
    PostgreSQL Server와 Client와의 접속에는 처음 Client가 접속을 하게 되면   
    pg_hba.conf에 대해 검색해서 해당 접속에 대한 접근허용을 확인하고 확인이 되면 이 Auth.Method에 설정된 암호화 방식으로 패스워드를 전송하라고 응답메시지를 보내고 다시 Client가 Server로 로그인을 하게 되는 방식입니다.        
    trust : 패스워드 없이 접근 가능      
    reject : 거부 
    md5 : 패스워드를 md5로 암호화해서 전송   
    crypt : crypt로 암호화 해서 전송 Postgres 7.2이후부터는 사용 않함. (이전버전설정 호환용)  
    password : text로 패스워드를 전송하는 것.  
    krb4, krb5 : KerberOS V4, 5를 지원한다.  
    ident : 접속 ClientOS User이름을 확인하는 방법?    
    pam : PAM(Pluggable Authentication Modules)서비스를 사용한 인증
  
- postgresql.conf 파일 관련 설명  
    postgres의 기본적인 설정 을 설정 할 수 있다.  
    특별하게 설정 할 값이 없다면 listen_addresses = '*' 부분만 이렇게 바꿔주도록 한다.

  
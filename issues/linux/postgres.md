# :newspaper: linux Centos 7 Postgresql 12 설치하기

## 설치 환경에서 외부망이 접속이 안될 경우
### 여기서 설치 파일 다운로드 필요!!
### [Linux Postgres 설치파일](https://github.com/ungseokchoi/feed/blob/master/issues/file/postgres)

## yum 을 통한 install
- Repository 업데이트   
  rpm -Uvh https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm    
  
- postgresql 12 설치  
  yum -y install postgresql12-server postgresql12-contrib   
  
## file 을 통한 install    
- 순서대로 명령어를 실행  
  sudo rpm -ivh postgres1.rpm   
  sudo rpm -ivh postgres2.rpm   
  sudo rpm -ivh postgres3.rpm   
  sudo rpm -ivh postgres4.rpm
  
## 기본 데이터 베이스 생성
- 
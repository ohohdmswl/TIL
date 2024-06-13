 📌 로컬에서 프로젝트 만든 후 깃에 init
 - 참고 url
	 - https://soda-dev.tistory.com/12
 - 깃 설치
 - 로컬에서 프로젝트 생성
 - 깃허브에서 프로젝트 저장할 저장소 생성
 - 프로젝트 폴더에서 (.git 폴더 만들 디렉토리) 깃 배시 실행
- 아래 코드 입력

```xml
git config --global user.name "유저이름"

git config --global user.email "유저 이메일"

git init      #.git 파일 생성

git add .     #선택한 프로젝트 폴더 내의 모든 파일 관리
				-> 특정파일만 하고 싶다면  git add 파일이름.파일형식  ex) git add a.txt

git status    #상태확인

git commit -m "주석"     #커밋

git remote add origin {위 3번에서 저장한 깃허브 저장소 주소}
git push -u origin master
```


📌 git ignore
- .git 폴더 있는 위치에 .gitignore 생성
- 깃 이그노어 생성 사이트
	- https://www.toptal.com/developers/gitignore
```xml
# Created by https://www.toptal.com/developers/gitignore/api/windows,java

# Edit at https://www.toptal.com/developers/gitignore?templates=windows,java

  

### Java ###

# Compiled class file

*.class

  

# Log file

*.log

  

# BlueJ files

*.ctxt

  

# Mobile Tools for Java (J2ME)

.mtj.tmp/

  

# Package Files #

*.jar

*.war

*.nar

*.ear

*.zip

*.tar.gz

*.rar

  

# virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml

hs_err_pid*

replay_pid*

  

### Windows ###

# Windows thumbnail cache files

Thumbs.db

Thumbs.db:encryptable

ehthumbs.db

ehthumbs_vista.db

  

# Dump file

*.stackdump

  

# Folder config file

[Dd]esktop.ini

  

# Recycle Bin used on file shares

$RECYCLE.BIN/

  

# Windows Installer files

*.cab

*.msi

*.msix

*.msm

*.msp

  

# Windows shortcuts

*.lnk

  

# End of https://www.toptal.com/developers/gitignore/api/windows,java

  
  

.project

.classpath

.settings

.setting

*/target

*/target/**

./*target/*

  

# Compliled files

target/

/target/

**/target

  

# setting files

#.classpath

#.project

.settings/

/.settings/

/bin/

.springBeans
```



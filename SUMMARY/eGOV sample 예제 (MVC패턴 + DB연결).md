📌 전자정부 프레임워크에서 샘플예제 프로젝트 생성
1. file - new - other - eGovFrame Web Project
2. project name, group id 입력 -  next
3. Generate Example 체크
4. Finish

📌 샘플 예제 실행
1. 톰캣 서버 설치
2. 톰캣 설정에 해당 프로젝트 추가시키고 인덱스 url 진입

📌 커스텀
1. dispatcherServlet 에서 component 설정 변경
	1. 사용하는 어노테이션이 exclude로 되어있다면 include로 변경
2. DB연결
	1. context-datasource
		1. 사용하는 db 정보 입력
			- driverClassName
			- url
			- username
			- password
	2. context-mapper
		1. sqlSession 설정
			- dataSource
			- configLocation (매퍼 설정 파일 위치 지정)
			- mapperLocations(매퍼 파일 위치 지정)
	3. context-sqlMap
		1. 아이바티스 사용시 사용하는 설정파일
		2. 마이바티스 사용하므로 삭제 또는 전체 주석
	4. pom
		1. db를 연결할 수 있는 라이브러리 추가
		2. dbcp 같이 추가
	5. 사용하지 않는 sample 소스 전체 주석



 

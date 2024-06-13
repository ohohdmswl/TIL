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

📌 이클립스 - 깃 연동
- they already exist in the workspace
- 이클립스의 깃 리포지토리에서 소스 클론
- 깃 리포지토리 패키지 익스플로러에서 import 진행하는데 계속 already 뜨면서 진행 안됨
- 소스트리로 먼저 해보고, 이클립스 자체에서 폴더 import 진행해도 동일하게 진행안됨
- target 같은 캐시 문제 의심해서 지우고 다시 진행해도 안됨
- 구글링 -> .project 에 프로젝트 이름 변경 후 정상 import
- 이클립스는 동일한 프로젝트이름이 있다면 import가 안됨
- 참고 url
	- https://withpie.tistory.com/entry/Eclipse-project-import-%ED%95%98%EB%A0%A4%EA%B3%A0%EB%B3%B4%EB%8B%88-already-Exist
	- 

 

- Misson 
	- **M_01**
		- ~~openLayers 라이브러리 사용(ver 5.3)~~
		- ~~vworld 띄워보기~~
		- ~~일반, 야간, 위성~~
	- **M_02**
		- geo server 익히기
		- 안양 db 사용
		- 집계구 데이터 쿼리 짜서 표출
		- 5179 -> 4326으로 변경해서 geo server  저장
		- 표출한 레이어에 읍면동 타이틀 뜰 수 있도록 스타일 지정

- 참고사항
	- vworld 지도 띄우는 방법
		- api 사용하는 방법
			- =>  vworld 가 권장하는 방식이지만 프로젝트는 이 방식으로 진행 X
		- 프로젝트에 사용한 방법(x, y, z) 사용해서 url으로 가져오기
			- => 프로젝트에 사용하는 방법

- openlayers 라이브러리
	- 공식문서 (https://openlayers.org/)
	- 빠른 시작 (https://openlayers.org/en/v5.3.0/doc/quickstart.html)

- Geo Server
	- [공식문서](https://geoserver.org/)
	- [[GIS] GeoServer를 설치해보자.](https://bongra.tistory.com/82)
	- [설치 및 실행](https://velog.io/@dailylifecoding/geoserver-install-and-start)
	- [GeoServer-기초](https://itstart-190126.tistory.com/entry/GeoServer-%EA%B8%B0%EC%B4%88)
	- [Layer Publishing](https://velog.io/@dailylifecoding/GeoServer-Layer-Publishing)

	- 앞서 생성한 `Store(저장소)` 에 있는 `Geometry 컬럼을 갖는 테이블` 이 존재한다면 위 그림처럼 목록에 표출
	- 




#GIS 
- 참고 url
	- [OpenLayers를 여행하는 개발자를 위한 안내서 - 4. QGIS 체험하기 - 𝝅번째 알파카의 개발 낙서장 (itcode.dev)](https://blog.itcode.dev/projects/2022/03/05/gis-guide-for-programmer-4)

🌏 **SHP(shape)**
- 대표적인 **공간정보 데이터 포맷**
- ESRI -> SHP, QGIS 고안
- 일반 데이터 컬럼 :  데이터 형식 맞게 저장(varchar, number, date...)
- 위치 정보: 정해진 규격으로 저장(해당 바이너리 통해 데이터의 형식 및 좌표 데이터 산출 가능)
- **SHP 파일 구성요소**(4가지)
	- **shp** (벡터 도형 데이터)
	- shx (벡터 도형 인덱스)
	- dbf (각 도형 속성 데이터)
	- prj (좌표 정보)

🌏 **GeoJSON**
- 공간 정보를 표현하기 위해 정해진 방식으로 구성된 JSON
- HTTP 통신으로 공간정보를 쉽게 호출하는데 사용

🌏 **파라미터**

| 파라미터        | 의미                       |
| ----------- | ------------------------ |
| `proj`      | 투영체                      |
| `a`         | 장반경(타원에서 가장 긴 반지름)       |
| `b`         | 단반경(타원에서 가장 짧은 반지름)      |
| `lat` `lon` | 좌표계의 기준 경위도 (경:세로 ,위:가로) |
| `x` `y`     | 좌표계의 기준 xy               |
| `k`         | 좌표계 배율                   |
| `ellps`     | 타원체 종류                   |
|             |                          |



🌏 **QGIS**
- [QGIS 프로젝트에 오신 것을 환영합니다!](https://qgis.org/ko/site/)
- https://docs.qgis.org/3.10/en/docs/
- https://m.blog.naver.com/PostView.naver?blogId=flyproject&logNo=221959825488&targetKeyword=&targetRecommendationCode=1&fromRecommendationType=POPULAR_POST&targetRecommendationDetailCode=1000
- https://dynamic-programmer.tistory.com/entry/QGIS-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C-%EB%B0%8F-%EC%84%A4%EC%B9%98-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95-%EC%A7%80%EB%8F%84-%EA%B3%B5%EB%B6%80
- 서울 행정구역 shp 파일
	- https://www.vworld.kr/dtmk/dtmk_ntads_s002.do?dsId=30604
	![image](https://github.com/ohohdmswl/TIL/assets/132552661/18b771ab-a80d-4cef-8d01-f750f5b236a7)

- 공간정보데이터 SHP를 사용가능한 툴
- 오픈소스
- <-> ArcGIS


🌏 **OSM (Open Street Map)**
- 자율적으로 관리하는 세계지도
- 가급적으로 맨 밑에 두어 베이스로 사용해야 다른 요소 확인 편함
- 







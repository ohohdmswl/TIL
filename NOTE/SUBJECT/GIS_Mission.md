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
	- [GeoServer를 활용하여 지도(레이어)를 발행 및 화면에 표출 해보자. (1)( feat. OpenLayers )](https://bongra.tistory.com/85)
	- [GeoServer를 활용하여 지도(레이어)를 발행 및 화면에 표출 해보자. (2)( feat. OpenLayers )](https://bongra.tistory.com/86)
	- [geoserver 맵 발행 및 openlayers 연동.](https://zzang9iu.tistory.com/26)
	- [OpenLayers + GeoServer + PostGIS + VWORLD + WFS,WMS](https://dgblog.tistory.com/260)



- SLD
	- [Geoserver에서 layer sytle 적용해보기](https://wldnjd2.tistory.com/30) 
	- 저장된 지도 레이어 스타일을 갖는 xml 형식 파일
	- 래스터, 백터 데이터를 포함하고 라벨, 색상, 글꼴 등 기타정보 포함
	- SDL 파일 수정 -> 레이어 스타일링 가능
	- [geo style](https://wogus789789.tistory.com/316)
	- [Geoserver WMS 라벨 스타일(TextSymbolizer) 설정 팁](https://yoginsoft.tistory.com/8)
	- [텍스트 심볼라이저](https://docs.geoserver.org/stable/en/user/styling/sld/reference/textsymbolizer.html)
	- https://groups.google.com/g/osgeo-kr/c/O-IQXO2RoDw
	- 
- 프록시
	- [geoserver + openlayers cors 문제 해결방법](https://devhoma.tistory.com/108)
	- 로컬에서 할 때는 프록시 안해도 인터넷 잘 되니까 상관없는데 서버 올리거나 할 때는 프록시를 해야한단다
	- 일단 재끼고 로컬에서 진행 하고 추후에 프록시 태우는걸 연습해보도록 하자
	- 


- 좌표계 변경
	- https://pjs21s.github.io/geoserver-setting/


- GeoServer style (라벨)
	- [라벨 다 보이게 설정 옵션](https://bongra.tistory.com/425)
```xml
<!-- 라벨이 모든 줌레벨에서 보이도록 하는 옵션 -->
<se:VendorOption name="spaceAround">-1</se:VendorOption>
<se:VendorOption name="conflictResolution">false</se:VendorOption>
<se:VendorOption name="goodnessOfFit">0</se:VendorOption>
```

```xml
<?xml version="1.0" encoding="EUC-KR"?>
<StyledLayerDescriptor version="1.0.0"
  xsi:schemaLocation="http://www.opengis.net/sld http://schemas.opengis.net/sld/1.0.0/StyledLayerDescriptor.xsd"
  xmlns="http://www.opengis.net/sld" xmlns:ogc="http://www.opengis.net/ogc"
  xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">

  <NamedLayer>
    <Name>prct_yj_image</Name>
    <UserStyle>
      <Title>A violet polygon style</Title>
      <FeatureTypeStyle>
        <Rule>
          <Title>violet polygon</Title>
          
          <TextSymbolizer>
             <Geometry>
            	<ogc:Function name="centroid">
              		<ogc:PropertyName>geom</ogc:PropertyName>
             	</ogc:Function> 
              </Geometry>
          	<Label>
            	<ogc:PropertyName>emd_kor_nm</ogc:PropertyName>
          	</Label>
            <Font>
              <CssParameter name="font-family">맑은 고딕 Bold</CssParameter>
              <CssParameter name="font-size">8</CssParameter>
              <CssParameter name="font-style">normal</CssParameter>
              <CssParameter name="font-weight">bold</CssParameter>
            </Font>
          </TextSymbolizer> 
          <PolygonSymbolizer>
            <Fill>
              <CssParameter name="fill">#fabbef</CssParameter>
              <CssParameter name="fill-opacity">0.5</CssParameter>
            </Fill>
            <Stroke>
              <CssParameter name="stroke">#000000</CssParameter>
              <CssParameter name="stroke-width">0.5</CssParameter>
            </Stroke>
          </PolygonSymbolizer>

        </Rule>

      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```


- 다른 함수 사용
```xml
<?xml version="1.0" encoding="EUC-KR"?>
<StyledLayerDescriptor version="1.0.0"
  xsi:schemaLocation="http://www.opengis.net/sld http://schemas.opengis.net/sld/1.0.0/StyledLayerDescriptor.xsd"
  xmlns="http://www.opengis.net/sld" xmlns:ogc="http://www.opengis.net/ogc"
  xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">

  <NamedLayer>
    <Name>prct_yj_image</Name>
    <UserStyle>
      <Title>A violet polygon style</Title>
      <FeatureTypeStyle>
        <Rule>
          <Title>violet polygon</Title>
          
          <TextSymbolizer>
             <Geometry>
            	<ogc:Function name="centroid">
              		<ogc:PropertyName>geom</ogc:PropertyName>
             	</ogc:Function> 
              </Geometry>
          	<Label>
            	<ogc:PropertyName>emd_kor_nm</ogc:PropertyName>
          	</Label>
            <Font>
              <CssParameter name="font-family">맑은 고딕 Bold</CssParameter>
              <CssParameter name="font-size">8</CssParameter>
              <CssParameter name="font-style">normal</CssParameter>
              <CssParameter name="font-weight">bold</CssParameter>
            </Font>
          </TextSymbolizer> 
          <PolygonSymbolizer>
            <Fill>
              <CssParameter name="fill">#fabbef</CssParameter>
              <CssParameter name="fill-opacity">0.5</CssParameter>
            </Fill>
            <Stroke>
              <CssParameter name="stroke">#000000</CssParameter>
              <CssParameter name="stroke-width">0.5</CssParameter>
            </Stroke>
          </PolygonSymbolizer>

        </Rule>

      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>

```

- [라벨 여러개 표출됨](https://bongra.tistory.com/336)

select * from 'table' where ym =%ym%


${ym}



- 타일로 가져오면 중복이 생겨서 라벨이 중복으로 생김
- 중복 방지하려면 tile로 가져오지 말고 image로 가져와야한다
- [참고한 소스](https://openlayers.org/en/v4.6.5/examples/wms-image.html?q=image)
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Single Image WMS</title>
    <link rel="stylesheet" href="https://openlayers.org/en/v4.6.5/css/ol.css" type="text/css">
    <!-- The line below is only needed for old environments like Internet Explorer and Android 4.x -->
    <script src="https://cdn.polyfill.io/v2/polyfill.min.js?features=requestAnimationFrame,Element.prototype.classList,URL"></script>
    <script src="https://openlayers.org/en/v4.6.5/build/ol.js"></script>
  </head>
  <body>
    <div id="map" class="map"></div>
    <script>
      var layers = [
        new ol.layer.Tile({
          source: new ol.source.OSM()
        }),
        new ol.layer.Image({
          extent: [-13884991, 2870341, -7455066, 6338219],
          source: new ol.source.ImageWMS({
            url: 'https://ahocevar.com/geoserver/wms',
            params: {'LAYERS': 'topp:states'},
            ratio: 1,
            serverType: 'geoserver'
          })
        })
      ];
      var map = new ol.Map({
        layers: layers,
        target: 'map',
        view: new ol.View({
          center: [-10997148, 4569099],
          zoom: 4
        })
      });
    </script>
  </body>
</html>
```

- imageLayer 사용시 js오류 발생했음 ㅠ
- tile -> imageLayer -> image 변경 후 정상 표출 확인
- vworld는 타일로 가져와도 상관없는데 레이어는 통 이미지로 가져와야 정상적으로 중복없이 표출됨

- 테이블로 레이어 발행하는게 문제라고 해서 sql view로 가져왔지만 동일 오류 발생
- 테이블로 불러온 레이어도 통이미지로 가져오면 중복없이 정상적으로 가져옴
- 레이어를 tile말고 Image / ImageWMS로 가져오도록 하자


그렇다면 vworld는 타일로 가져와도 되나?
양주 소스는 vworld는 타일로 가져오고 밑에 레이어만 image로 가져온다아아아아아




- 포인트 아이콘으로 png 넣기
	- [url](https://gis.stackexchange.com/questions/122654/geoserver-sld-external-graphic-path) 처럼 아예 gis 경로에 강제로 박아도 됨
	- 이미지 삽입 아이콘 버튼 클릭해서 이미지 선택하면 gis 경로에 알아서 추가 되더라 (sld 스타일 폴더에 같이 있더라)


- geoserver 파라미터 (parameters)
- [sql view 로 레이어 만들고 파라미터 초기화](https://docs.geoserver.geo-solutions.it/edu/en/adding_data/add_sqllayers.html)
- https://wogus789789.tistory.com/324
- https://docs.geoserver.org/2.22.x/en/user/data/database/sqlview.html
- https://itstart-190126.tistory.com/entry/OpenLayers-GeoServer-SQL-View-parameteric-SQL-View
- https://yoginsoft.tistory.com/5
- https://wogus789789.tistory.com/321
- https://itstart-190126.tistory.com/entry/GeoServer-SQL-View-parametric-SQL-View-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0
- 



```sql
select * from 'table' where ym =%ym%
${ym}

select * from 'table' where ym ='%ym%'
#{ym}

<!-- 이렇게 하면 숫자로 인식 -->
WHERE sdd.data_crtr_pnttm >= %startDate%


```



- [div 위에 div 올리기](https://velog.io/@ljo094822/div%EC%9C%84%EC%97%90-div%EC%98%AC%EB%A6%AC%EA%B8%B0)
	- 아래에 있을 div(부모): positon :relative;  
	- 위로 위치할 div(자식): position: absolute;


- openlayer
	- [vector](https://mollangpiu.tistory.com/254)
		- 지도의 좌표를 저장하는 object
		- 저장하거나 불러올 때 vector 사용
		  
	- [map 객체](https://openlayers.org/en/latest/apidoc/module-ol_Map-Map.html)
		- 지도 랜더링 위해 -> 뷰, 레이어, 컨테이너 필요
		![image](https://github.com/user-attachments/assets/137b1b22-c052-4dd3-80e9-769d9a94fb3a)
		- target : 맵의 컨테이너, 지도 표출할 요소의 id, 
		- view : 지도의 뷰
		- layers : 레이어, 없으면 레이어 없는 맵 랜더링 됨, 레이어는 순서대로 랜더링, 가장 마지막에 랜더링 하는 레이어가 가장 위에서 보임
		- [singleClick](https://openlayers.org/en/latest/apidoc/module-ol_MapBrowserEvent-MapBrowserEvent.html#event:singleclick) : 싱글클릭(이벤트)
		- [moveend](https://openlayers.org/en/latest/apidoc/module-ol_MapEvent-MapEvent.html#event:moveend) : 지도가 이동된 후에 발생(이벤)
		- set : set(key, value, silent), 값 세팅(Sets a value.)
		  
	- [view 객체](https://openlayers.org/en/latest/apidoc/module-ol_View-View.html)
		- view 객체는 지도의 간단한 2d 뷰 표출
		- 지도의 중심, 해상도, 회전 변경하는데 사용하는 객체
		- projection : 투영, 중심의 좌표계를 결정하고 그 단위는 해상도단위 (투영단위) 결정, 기본 값 EPSG:3857
		- view의 상태
			- center(getCenter, setCenter)
			- resolution(getResolution, setResolution) : 뷰의 초기 해상
			- rotation(getRotation, setRotation)
			- 각 상태에는 getter, setter 존재
		- state zoom은 실제 뷰에 저장 안됨 -> 모든 계산은 내부적으로 resolution 상태 사용
		- but setZoom, getZoom 사용 가능
		- getResolutionForZoom, setResolutionForZoom 사용해 시스템 전환 가능
		- resoluitions : 지정된 경우 확대 수준 결정하는 해상도(배열), 정해놓으면 해당 해상도로 확대가 가능한가 봄

- map 전체 프로퍼티 값 알고 싶을 때
```js
	$(function(){
	    var ulHtml = "";
		ulHtml += "<ul>";
		ulHtml += "<li>";
		ulHtml += "<a href='./pubTransMenu1.do?ctCode="+"CT41370244"+"&sitemapCode="+$("#sitemapCode").val()+"'>기초정보</a>"
		ulHtml += "</li>";
		ulHtml += '<li>';
		ulHtml += "<a href='#'  class='active'>노선분석</a>";
		ulHtml += "</li>";
		ulHtml += "<li>";
		ulHtml += "<a href='./pubTransMenu2.do?ctCode="+"CT41370244"+"&sitemapCode="+$("#sitemapCode").val()+"'>수요분석</a>"
		ulHtml += "</li>";
		ulHtml += "</ul>";
		$(".sub_gnb_title").append(ulHtml);
		
		console.table(map);
	})

// console.log, console.table 사용해서 객체 값 확인하기
console.table(map); 
```

![image](https://github.com/user-attachments/assets/80c85ce4-8291-4b01-8206-4d3909e8da71)

- 새로 gisYjPbTrns2.jsp 생성하고 오류가 없는데 vworld 지도가 표출되지 않았던 이유
	- 참고소스에서는 map객체 생성할 때 mapView 객체를 같이 생성해서 신경쓰지 않아도 되지만,  지금 작성하는 코드는 map객체와 mapview 객체를 따로 생성하고 사용함
	- 근데 map객체에서 view라는 속성을 지정할 때 mapView 객체를 사용하게 되니까 map 객체 선언하기 전에 mapView 객체를 먼저 생성해야함
	- 그리고 map 객체에서 layers를 빈 배열상태로 두고 addLayer 메소드를 사용해서 레이어를 추가해야함


- openlayer [data 설명(파람)](https://exhibitlove.tistory.com/133)

[ol/layer/Image](https://openlayers.org/en/latest/apidoc/module-ol_layer_Image.html)
[ol/source/ImageWMS](https://openlayers.org/en/latest/apidoc/module-ol_source_ImageWMS.html)~ImageWMS


-[getGetFeatureInfoUrl (좌표, 해상도, 투영, 매개변수)](https://openlayers.org/en/v3.20.1/apidoc/ol.source.ImageWMS.html#getGetFeatureInfoUrl)
-  [ol](https://openlayers.org/en/v3.20.1/apidoc/ol.html) [.source](https://openlayers.org/en/v3.20.1/apidoc/ol.source.html) .ImageWMS 의 메소드
- gis_main에 있는 getGetFeatureInofo => api에 존재하는 메소드
- 전달된 좌표, 해상도, 투영 관한 getFeatureInfo URL 반환 -> url 구성 못할 경우 return : undefined 

evt.coordinate
	- 클릭이나 싱글 클릭과 같은 이벤트가 발생한 지도上的 점의 좌표를 의미
	- 사용자가 지도를 클릭하면 OpenLayers는 이벤트를 캡처하고 그 위치의 좌표를 제공
	- 이러한 좌표는 일반적으로 지도의 기본 투영 시스템(보통 EPSG:3857)으로 제공

```js
map.on('singleclick', function(evt){ 
	var coordinate = evt.coordinate; 
	console.log(coordinate); 
});
```

- `evt.coordinate`는 사용자가 클릭한 위치의 [x, y] 좌표를 반환
- 이 좌표는 마커를 배치하거나 클릭한 위치에 대한 정보를 가져오거나 `ol.proj.transform()`과 같은 함수를 사용하여 다른 투영 시스템으로 변환하는 등 다양한 용도로 사용 가능
- Stack Overflow에서 OpenLayers에서 좌표를 얻는 방법에 대한 논의
- - [Stack Overflow에서 OpenLayers에서 좌표를 얻는 방법에 대한 논의](https://stackoverflow.com/questions/51142610/get-coordinates-event-map-openlayers-4-6-5-5)
- [Geographic Information Systems Stack Exchange에서 OpenLayers 이벤트에 대한 논의](https://gis.stackexchange.com/questions/134441/stop-openlayers-3-map-firing-click-event-after-dragging)


－ 클릭한 지점 정보가져오는 url 만들고 조회하면 cors 오류 생겨서 wms 타일 만들 때 아예 설정(이때 요청을 보낸 곳은 내 컴퓨터(local)이고 요청을 받은 곳은 웹 서버였기 때문에 생긴 크로스 도메인 오류였다.)
	- 방법
		1. 프록시 태우기
		2. wms 생성시 crossOrigin 파람 추가 (crossOrigin : anonymous)
			1. https://yd-dev.tistory.com/5
			2. https://thinkoutbox.tistory.com/56
			3. https://wogus789789.tistory.com/319?category=891011


－생각생각
	－ 프로젝트는 해당 지역 값、 지역 이름 선택시에 선택한 지역에 맞는 위치 경계가 지도에 표출됨
	－ 그래서 레이어가 모두 꺼져있어도 가져올 값이 존재할 수 있다고 생각함
		－ 선택 값에 읍면동 코드를 넣으면 되니까¿
	－ but 지금은 선택을 지도에서 하고 그 값을 가지고 select 표출을 해야함
		- 그랬을 때 내가 생각하기엔
			- 스타일 표출을 하지 않는 기본 읍면동 레이어가 있는거임
			- 스타일만 표출을 안할 뿐이지, 레이어 자체는 visible true 로 해서.
			- 읍면동 레이어를 그럼 두개 만들어야겠다. 
			- 근데 그러면.. config를 어떻게 해야하지.. 
	

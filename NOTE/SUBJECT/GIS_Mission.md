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




```sql
select * from 'table' where ym =%ym%
${ym}

select * from 'table' where ym ='%ym%'
#{ym}

```

#zTree #JSlib
###### 공식 URL
- https://www.treejs.cn/v3/main.php#_zTreeInfo
- https://github.com/zTree/zTree_v3
	- 공식 GIT URL의 DEMO에서 예제 소스 확인 가능

## How to use zTree 
### 1. Tree 생성
##### 1. zTree 생성할 html 요소 작성
-  `<ul>` 태그 사용
  ```html
<div class="zTreeDemoBackground left">
	<ul id="treeDemo" class="ztree"></ul>
</div>
```

##### 2. zTree 데이터 설정
- 데이터 생성 방법 (2가지)
	- 부모 - 자식 관계 충족 방법
	- <u>simpleData 방법</u>
```js
var setting = {
	data: {
		simpleData: {
			enable: true,
			idKey: "id",
			pIdKey: "pId",
			rootPId: 0
		}
	}
};

var treeNodes = [
    {"id":1, "pId":0, "name":"test1"},
    {"id":11, "pId":1, "name":"test11"},
    {"id":12, "pId":1, "name":"test12"},
    {"id":111, "pId":11, "name":"test111"}
];
```

##### 3. zTree init
```js
$(document).ready(function(){
			$.fn.zTree.init($("#treeDemo"), setting, treeNodes);
});
```


### 2. zTree setting
##### 1. setting 종류
	- async
	- callback
	- check
	- data (keep, key, simpleData, render)
	- edit (drag)
	- view

- ###### 사용한 setting 속성
```js
var setting = {
		data: {
			simpleData: {enable: true} //간단한 데이터 형식을 허용 여부(default : false)
		},
		view: {
			selectedMulti: false		//중복선택 - (default : true) -> false로 중복 선택 방지
			,showIcon: true				//노드 아이콘  show
			,nameIsHTML: false			//html 태그 허용금지 ex.{"name":"<font color='red'>test</font>"}
		},
		callback: {
			onClick: fncC //트리 클릭시 동작 콜백
// 			,beforeEditName: fncR  //트리 이름 변경 전 콜백
			,beforeEditName: fncB	//로그인 여부 확인 후 이름변경 진행
			,onRename: fncR
			,beforeRename: fncR  //이름변경 콜백
		},
		edit: {editNameSelectAll: true}, 	//이름변경시 이전 이름 전체선택 되도록
		keep: {parent: true}, 				 //상위 노드의 하위 노드를 모두 제거해도 해당 'isParent' 속성이 여전히 true를 유지
		view: {fontCss: getFont} //use_yn 'N'일 경우 -> 취소선
};//setting	
```


### 3. zTree 표출
##### 1. treeData 가져오기
<h6>1. ajax 사용하여 treeData 가져오기</h6>
1. ajax로 CTR 연결해 DB에서 사용할 treeData 가져오기 
2. 데이터 가져온 방법 
    + `List<List<Map<String, Object>>>` 사용 
	+ 3가지의 트리를 표출해야 함 
    + `List<Map<String, Object>>` 형식의 List * 3 
    + 3개의 리스트를 새 List에 담아서 return 
3. json 타입으로 data 가져와서 jsp로 넘기기 
    - jsonView 사용 
    - return type: ModelAndView



<h6>2. ajax (success)</h6>
	**1.  treeData 가공**
		- 데이터 가공함수(treeData)
			- 데이터 가공함수 인자로 treeData 사용
	**2. zTree init**
	**3. zTree 표출**
		1. zTree를 표출할 html 요소에 할당
		2. 처음 표출시 모든 노드를 확인할 수 있도록 설정
			- `expandAll(true)` 메소드 사용
	   
<h6>3. 데이터 가공함수(treeData)</h6>
	1. treeData 담을 배열 선언
	2. 가져온 데이터의 key 맞게 for 반복문 사용하여 json data 객체 생성
	3. 노드 부모 속성 설정
	4. 노드 아이콘 변경
	5. 최상위 노드 항상 open 설정
	6. for 반복문 사용한 treeData 를 `push` 메소드 사용하여 추가

```js
//트리데이터 담을 배열
var jsonTree = [];

//트리데이터 가공을 위한 for 반복문
for (var i = 0; i < jsonData.length; i++) {
	var col01 = jsonData[i]["col01"];
	var col02 = jsonData[i]["col02"];
	var col03 = jsonData[i]["col03"];

	//트리노드 객체 생성
	var obj = {
			  "col01": col01,
			  "col02": col02,
			  "col03": col03
			};

	//트리 노드 (부모 속성 설정(isParent), 아이콘 변경(icon))
	if(col01==null || col01==''){	
		obj["isParent"] = true;
	}else{
		obj["icon"] = '${pageContext.request.contextPath }/images/file.png';
	}
	//최상위 노드일 경우 (오픈 설정(open))
	if(col02==0){	
		obj["open"] = true;
	}

	//가공한 트리데이터 obj객체에 추가
	//트리데이터를 for 반복문 통해 하나씩 가공해서 obj객체에 넣고 해당 
	jsonTree.push(obj);
};

//가공된 트리데이터 리턴
return jsonTree;

```


### 4. zTree 노드 수정
##### 1. node 추가
##### 2. node 수정(이름 변경)
##### 3. node 삭제





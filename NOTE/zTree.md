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
1. ajax 사용하여 treeData 가져오기
	1. ajax로 CTR 연결해 DB에서 사용할 treeData 가져오기
	2. 데이터 가져온 방법
		-  List<List<Map<String, Object>>> 사용
			- 3가지의 트리를 표출해야
				- List<Map<String, Object>> 형식의 List * 3
				- 3개의 리스트를 새 List에 담아서 return
	1. json 타입으로 data 가져와서 jsp로 넘기기
		- jsonView 사용
			- return type : ModelAndView
		-


#zTree #JSlib
###### 공식 URL
- https://www.treejs.cn/v3/main.php#_zTreeInfo
- https://github.com/zTree/zTree_v3
	- 공식 GIT URL의 DEMO에서 예제 소스 확인 가능

## How to use zTree 
### 1. Tree 생성
1. **zTree 생성할 html 요소 작성**
-  `<ul>` 태그 사용
  ```html
<div class="zTreeDemoBackground left">
	<ul id="treeDemo" class="ztree"></ul>
</div>
```

2. **zTree 데이터 설정**
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

3. zTree init
```js
$(document).ready(function(){
			$.fn.zTree.init($("#treeDemo"), setting, treeNodes);
});
```


### 2. zTree setting
1. 
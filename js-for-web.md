
## Javascript for Web

### classList

| 속성 | 설명 |
|---|---|
| `add` | 지정한 클래스 값을 추가, 만약 추가하려는 클래스가 존재한다면 무시 |
| `remove` | 지정한 클래스 값을 제거 |
| `item` | 콜렉션의 인덱스를 이용하여 클래스값을 반환 |
| `toggle` | 클래스가 존재하면 제거, 존재하지 않으면 추가 |
| `contains` | 지정한 클래스 값이 Element의 속성에 존재하는지 학인함 |
| `replace` | 존재하는 클래스를 새로운 클래스로 교체 |


```javascript
addBtn.classList.add('active');
addBtn.classList.contains('active');
addBtn.classList.replace('oldActive', 'newActive');
```

**[⬆ back to top](#table-of-contents)**


### 이벤트 위임



**[버블링과 캡처링에 대해 이해를 얻은 캡틴 판교님의 글](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)**

#### 이벤트 버블링(Event Bubbling)
이벤트 버블링은 특정 요소에서 이벤트가 발생했을 때 
해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성을 의미한다

```html
<body>
	<div class="one">
		<div class="two">
			<div class="three">
			</div>
		</div>
	</div>
</body>
```

```javascript
var divs = document.querySelectorAll('div');
divs.forEach(function(div) {
	div.addEventListener('click', logEvent);
});

function logEvent(event) {
	console.log(event.currentTarget.className);
}
```

#### 이벤트 캡쳐(Event Capture)
이벤트 캡쳐는 이벤트 버블링과 반대 방향으로 진행되는 이벤트 전파 방식입니다




**[⬆ back to top](#table-of-contents)**

### DOM 탐색

노드는 HTML 문서내 구조를 이루고 있는 요소를 말한다.  
HTML 문서의 요소는 부모, 자식, 형제 구조를 이루므로 **특정 요소를 기준** 삼아서 서로 상대적으로 참조할 수 있다. 

| 속성 | 설명 |
|---|---|
| `parentNode` | 부모 노드를 선택합니다. |
| `children` | 자식 노드를 선택합니다. |
| `previousSibling` | 이전 형제를 선택합니다. |
| `nextSibling` | 다음 형제를 선택합니다.  |


**[⬆ back to top](#table-of-contents)**


### Node 생성/삽입/삭제

| 속성 | 설명 |
|---|---|
| `createElement(요소 이름)` | 새로운 요소 노드 객체를 생성 |
| `appendChild(삽입할 노드)` | 인자로 넘긴 노드를 마지막 자식 노드로 삽입 |
| `removeChild(자식 노드)` | 노드에서 인자로 넘긴 자식 노드를 삭제 |
| `replaceChild(새로운 노드, 자식노드)` | 인자로 받은 자식 노드를 제거하고, 새로운 노드로 바꿈  |


**[⬆ back to top](#table-of-contents)**


### Storage 메서드

| 속성 | 설명 |
|---|---|
| Storage.setItem() | 인자로 key, value를 전달해 Storage에 저장 |
| Storage.getItem() | 인자로 key를 전달하여 Storage에 저장된 값을 조회 |
| Storage.removeItem() | 인자로 key을 전달하면 해당 키가 Storage에서 지워짐 |
| Storage.clear() | Storage 전체를 비움 |


### localStorage에 데이터 넣어보기
`localStorage`에 데이터를 저장할 때 key/value 형식으로 저장할 수도 있지만, 객체 형태로 저장하려면 `JSON.stringify()`를 통해 객체 타입을 문자열 타입으로 변환하여 저장해야 한다. 또한 반대로 `localStorage`의 데이터를 가져올 때는 `JSON.parse()`를 통해 문자열을 객체 타입으로 변환하여 가져와야 합니다. 

```javascript
const TODOS_LS = "toDos";
const toDos = [];

for (let i = 0; i < 5; i++) {
  const toDoObj = {
    text:"안녕하세요",
    id: i + 1
  }
  toDos.push(toDoObj);  
}

localStorage.setItem(TODOS_LS, JSON.stringify(toDos))
```


### localStorage 활용

#### JSON.stringify
`localStorage.setItem(TODOS_LS, toDos)`처럼 `setItem()`메소드의 인자에 자바스크립트 데이터를 직접 넣으면 `LocalStorage`에는 `[object Object]`처럼 데이터가 들어간다.

왜냐하면 `LocalStorage`에는 자바스크립트의 data를 저장할 수 없기 때문이다. `LocalStorage`는 모든 데이터를 `string`으로 저장한다. 그래서 자바스크립트 `object`가 `string`이 되도록 바꾸고 저장해야 한다. 이를 위해서 `JSON.stringify()`메소드를 사용해야 하는데, `JSON.stringify()`는 인자로 전달된 자바스크립트 `object`를 `string`으로 바꿔준다.

```javascript
function saveToDos(){
  localStorage.setItem(TODOS_LS, JSON.stringify(toDos));
}
```

#### JSON.parse
`localStorage.getItem()`으로 데이터를 불러온 경우 불러온 데이터가 `string`이라는 문제가 생긴다! 이를 자바스크립트에서 활용하기 위해서는 `JSON(Javascript Object Notation)`을 사용해야 한다! JSON을 통해 string을 object로, object를 string으로 변경할 수 있다.

`JSON.parse()`를 사용하면 데이터를 가져올 때 자바스크립트가 다룰 수 있도록 `string`을 `object`로 바꿔준다!

아래는 `localStorage`에서 가져온 코드를 `JSON.parse()`메서드를 통해 `string`을 `object`로 바꾸었다.

```javascript
function loadToDos() {
  const loadedToDos = localStorage.getItem(TODOS_LS);
  if(loadedToDos !== null) {
    const parsedToDos = JSON.parse(loadedToDos);

    parsedToDos.forEach(toDo => {
      paintToDo(toDo.text);
    });
  } 
}
```

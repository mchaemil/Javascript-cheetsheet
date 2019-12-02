# Javascript CheetSheet :page_facing_up:


### Javascript
개발자 haemil 입니다.  
본문서(:page_facing_up:)는 학습한 Javascript의 내용을 정리해놓는 CheetSheet 입니다.  
구조적이고, 읽기 쉬운 문서를 작성하기 위해 고민을 한아름 껴안고 있는 중이니.. 아직은 내용물이 별로 없을지라도 이해해주세요. 찾아주셔서 감사합니다.

:ballot_box_with_check: 1.   
:white_check_mark: 2. 

## Table of Contents

  1. [Variable](#variable)
  1. [Control Structures](#Control Structures)
  1. [References](#references)
  1. [Objects](#objects)
  1. [Arrays](#arrays)
  1. [Destructuring](#destructuring)


---

## Variable
프로그래밍을 잘 하기 위해서는 값을 다루는 능력이 중요하다. 이를 위해 프로그래머는 변수를 사용하여 값(데이터)에 이름을 붙이고, 그 이름을 통해서 값을 읽거나 사용할 수 있다. 
```javascript
var num = 1;
const str = 'hello world';
```
Javascript는 두 가지의 데이터 타입이 존재하는데, Primitive와 Object가 그 주인공이다. Javascript는 실행할 때 변수에 저장된 데이터 타입이 다른 타입으로 변경될 수 있으므로 프로그램을 실행할 때 혹시 모를 타입 변환에 주의해야 한다. 
- Primitive: `Number`, `String`, `Boolean`, `null`, `undefined`
- Object:  `Object`, `Function`, `Array`, `Date`, `등...`

Javascript 에서 변수는 ES5 키워드 `var`, ES6의 키워드 `const`, `let` 을 통해서 선언할 수 있는데, 변수의 누수현상(블록 범위를 지나도 변수가 살아있는)을 방지하기 위해서는 ES6의 키워드를 사용하는 것이 권장된다.

```javascript
if(true) {
  var hi_1 = 'hello'; // bad
}
if(true){
  let hi_2 = 'hello'; // good
}
console.log(hi_1); // => 'hello';
console.log(hi_2) // "ReferenceError: hi_2 is not defined

```

글쓴이는 이제 더 이상 `var`를 사용하지 않는다. 이를 통해 **1.변수의 유효범위를 생각하며** 코드를 작성하게 되었고, `const` 사용을 통해 **2.변수의 오염 가능성을 방지**할 수 있게 됐다. 
```javascript
let hasDuplicate = false;
const item = document.querySelector('.item')
```

Javascript는 primitive type을 빼고 모든 값이 Object type이며, 객체 리터럴과 생성자로 생성할 수 있다.  
- Object:  `Object`, `Function`, `Array`, `Date`, `등...`

airbnb Javascript Style Guide에서는 객체를 생성할 때 객체 리터럴 방식을 채택한다. 
> (Use the literal syntax for object creation)  

글쓴이도 이를 따라서 객체를 생성할 때 리터럴(Use the literal) 방식을 채택하려 한다. 그 이유로는 리터럴로 정의한 객체는 끌어올리지 않기 때문이다. (not hoisting)

```javascript
const arr = [1,2,3];
const obj = {};
const plus = function(a, b){
  return a + b
}

```

모두 객체 리터럴 형식으로 작성한다. 



- `null` : 프로그래머가 저장하는 값
- `undefined` : 컴퓨터가 던지는 값


## Control Structures

글쓴이가 Web 이라는 실행환경 위에서 자바스크립트로 한 가지 성장하게 된 코드는 아래와 같다. if문의 조건 속에 객체요소가 담겨있는지를 검사할 수 있게 되자 자바스크립트 나부랭이 신세를 면하게 되었다.


```javascript

let checkElement = false;

if(checkElement){
  // if 문에서 가장 중요한 것
  
}

```



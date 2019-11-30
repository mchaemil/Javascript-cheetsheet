# Javascript CheetSheet :page_facing_up:


### Javascript
개발자 haemil 입니다.  
본문서(:page_facing_up:)는 학습한 Javascript의 내용을 정리해놓는 CheetSheet 입니다.  
구조적이고, 읽기 쉬운 문서를 작성하기 위해 고민을 한아름 껴안고 있는 중이니.. 아직은 내용물이 별로 없을지라도 이해해주세요. 찾아주셔서 감사합니다.

:ballot_box_with_check: 1.   
:white_check_mark: 2. 

## Table of Contents

  1. [Variable](#variable)
  1. [References](#references)
  1. [Objects](#objects)
  1. [Arrays](#arrays)
  1. [Destructuring](#destructuring)


---

## Variable
프로그래밍을 잘 하기 위해서는 값을 다루는 능력이 중요하다. 이를 위해 변수를 사용하여 값(데이터)에 이름을 붙이고, 그 이름을 통해서 값을 읽거나 사용할 수 있다. 

동적타입 언어인 Javascript는 프로그램을 실행할 때 혹시 모를 타입 변환에 주의하여야 한다. 
```javascript
var num = 1;
const str = 'hello world';
console.log(num, str); // => 1 'hello world';
```
Javascript 에서 변수는 ES5 키워드 `var`, ES6의 키워드 `const`, `let` 을 통해서 선언할 수 있는데, 변수의 누수현상(블록 범위를 지나도 변수가 살아있는)을 방지하기 위해서는 ES6의 키워드를 사용하는 것이 권장된다.

글쓴이는 이제 더 이상 `var`를 사용하지 않는다. 이를 통해 **1.변수의 유효범위를 생각하며** 코드를 작성하게 되었고, `const` 사용을 통해 **2.변수의 오염 가능성을 방지**할 수 있었다. 

```javascript
var badNum = 1;
const str = 'hello world';

let isFlag = false;
```


`var` 대신 `const`, `let` 을 사용하고,  

```javascript
const arr = [1,2,3];
const obj = {};

```

모두 객체 리터럴 형식으로 작성합니다. 
- `Number`, `String`, `Boolean`, `Symbol`
- `Object`, `Function`, `Array`, `Date`



- `null`
- `undefined`

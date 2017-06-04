---
title: JavaScript ES6 문법 - 변수선언 let, const
date: 2016-12-25 01:54:47
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, let, const]
---

![JavaScript](/image/es6.png)

## ES6 변수, 상수 선언 키워드

`let` : 정의된 블록내에서만 존재하는 변수 선언 (지역 변수)
`const` : 위와 동일, 상수(변하지 않는 값) 선언

`var` : ES6문법 이전부터 사용하던 변수 선언 (전역 변수)

```
var x = 'global';	// 전역 변수
let y = 'global';	// 지역 변수
console.log(this.x); 	// "global"
console.log(this.y);	// undefined
```


### Scoping rules - `var`와 `let` 비교

```
function varTest() {
  var x = 1;
  if (true) {
    var x = 2; 		 // 위의 x와 같은 변수
    console.log(x); 	 // 결과 : 2
  }
  console.log(x); 	 // 결과 : 2
}
```

```
function letTest() {
  let x = 1;
  if (true) {
    let x = 2; 		 // 위의 x와 다른 변수
    console.log(x); 	 // 결과 : 2
  }
  console.log(x); 	 // 결과 : 1
}
```

### 내부함수 코드를 명확하게 해주는 `let`

```
var list = document.getElementById("list");

for (let i = 1; i <= 5; i++) { 	 // for문 내에서만 사용할 변수이므로 let 사용
  let item = document.createElement("li");
  item.appendChild(document.createTextNode("Item " + i));

  item.onclick = function (ev) {
    console.log("Item " + i + " is clicked.");
  };
  list.appendChild(item);
}
```

### 변수 선언 & 호이스팅 (2017-02-18 수정)

**var** : scope내 최상단으로 **호이스팅됩니다**.  
###### ※ 호이스팅 : 어떤 위치에 있든지 위로 끌어올려지는 현상
```
(function(){
    console.log(a); // var a 까지만 호이스팅되어 undefined
    var a = 10;   // 값 할당
    console.log(a); // 10
})();

```

**let**과 **const** : `TDZ (temporal dead zone, 임시사각지대)` 블락 스코프 내에서는 지역변수/상수에 대한 호이스팅이 이뤄지기는 하나, 선언된 위치 이전까지는 해당 변수/상수를 인식하지 못합니다.
###### 출처 : [고무곰님 블로그](https://gomugom.github.io/es6-for-react/index.html)


```
function do_something() {
  console.log(foo); 	// ReferenceError
  let foo = 2;
}

{
    let a = 2;
    {
        console.log(a); // 2일 것 같지만 이것도 error이다.
        let a = 3;
    }
}

```

### 전역변수 (2017-02-19 추가)

```
var a = 1;
window.a; // 1
delete window.a; // false

let b = 2;
window.b; // undefined

window.c = 3;
c; // 3
delete window.c; // true
c; // error c is not defined
```


`var a = 1;` 처럼 var로 변수를 선언하면 전역 변수가 되어 window 객체의 프로퍼티로 됩니다.
하지만 `delete window.a` 로 삭제를 하려고 해도 삭제를 할 수가 없습니다.

let은 전역변수가 아니므로 window 객체에 담기지 않습니다.
전역변수로 만들고 싶으면 `window.c = 3;`처럼 직접 window객체의 프로퍼티로 만듭니다.
이 때에는 `delete window.c;`로 지울 수 있습니다.



### 연관 링크
[let - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
[JavaScript Reference - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
[ECMAScript 6 Tutorial](http://ccoenraets.github.io/es6-tutorial/)

### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)

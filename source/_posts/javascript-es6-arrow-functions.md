---
title: JavaScript ES6 문법 - Arrow functions
date: 2016-12-26 13:52:09
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, arrow functions]
---

![JavaScript](/image/es6.png)

### Arrow functions(애로우 펑션, 화살표 함수 표현식)


화살표 함수 표현식(arrow function expression)은 함수 표현식(function expression)에 비해 **구문이 짧으며(예제 1.)**
this, arguments, super 또는 new.target을 **자체 바인딩하지 않습니다(예제 2.)**.

메소드가 아닌 함수에 가장 적합하며 **생성자로 사용할 수 없습니다(예제 3.)**

장점 : 브라우저 입장에서 함수를 받아들일 때 엔진으로 알아야 할 정보가 줄어들어, 성능이 좋아집니다.

##### 문법
```
(매개변수) => { statements } // 매개변수가 하나일 땐 괄호 생략 가능
() => { statements }        // 매개변수가 없는 함수는 괄호가 필요합니다.
_ => { statements }         // _를 쓰는 경우 위처럼 매개변수가 없다는 의미로 사용됩니다.

// 객체 리터럴을 return하는 경우는 body를 괄호속에 넣어야 합니다.
매개변수 => ({ foo: bar })
```

```
// 한줄일 경우 {}, return을 생략가능합니다.
var func = x => x * x;

// {} 를 쓴다면 return도 써야합니다.
var func = (x, y) => { return x + y; };
```

##### 예제 1. 짧은 문법 제공
```
var materials = [
  "Hydrogen",
  "Helium",
  "Lithium",
  "Beryllium"
];

var materialsLength1 = materials.map(function(material){
 return material.length
});

var materialsLength2 = materials.map((material)=>{
 return material.length
});

var materialsLength3 = materials.map(material=> material.length);
```

위 materialsLength1, materialsLength2, materialsLength3의 결과는 모두 `[8, 6, 7, 9]`로 같습니다.

##### 예제 2.

화살표함수의 this : 자기보다 상위 스코프의 this를 씁니다.

기존 JavaScript 문법의 `this`
```
function Person() {
  // Person () 생성자는`this`를 자신의 인스턴스로 정의합니다.
  this.age = 0;

  setInterval(function growUp() {
    // non-strict mode에서는 growUp()함수는 `this`를 정의합니다.
    // Person () 생성자에 의해 정의된 `this`와는 다른 전역(window) 객체로 정의됩니다.
    this.age++;
  }, 1000);
}

var p = new Person(); // age가 증가하지 않습니다.
```
위와 같은 문제를 해결하기 위해서 ECMAScript 3/5 문법에서는 아래와 같이 `this`를 변수에 저장하였습니다.
```
function Person() {
  var that = this;
  that.age = 0;

  setInterval(function growUp() {
    // callback은 `that`변수를 참조합니다.
    that.age++;
  }, 1000);
}

var p = new Person(); // age가 증가합니다.
```

혹은 bind를 사용하여 아래와같이 해결하기도 합니다.
```
function Person() {
  this.age = 0;

  setInterval(function growUp() {
    this.age++;
  }.bind(this), 1000);
}

var p = new Person(); // age가 증가합니다.
```

Arrow functions은 `this`를 자체 바인딩하지 않으므로 아래처럼 사용하면 예상대로 작동됩니다.
```
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // `this`는 Person객체를 제대로 참조합니다.
  }, 1000);
}

var p = new Person(); // age가 증가합니다.
```

##### 예제 3. (2017.02.27 추가)

![함수표현식과 화살표함수의 차이](/image/es6-arrow.png)

위 이미지는 크롬에서 함수표현식과 화살표함수의 차이를 보기 위한 코드입니다.
`function a(x, y)`에는 `prototype: Object`가 있고 `b(x,y)`에는 없습니다.
즉, 함수표현식은 프로토타입이 있기 때문에 생성자 함수가 될 수 있지만, 화살표 함수는 생성자 함수가 될 수 없습니다.


### 연관 링크
[Arrow functions - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)

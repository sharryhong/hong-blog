---
title: JavaScript ES6 문법 - Blocks and IIFEs
date: 2017-02-02 23:06:03
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, block, IIFE]
---

![JavaScript](/image/es6.png)

## Blocks and IIFEs

ES5 이하에서는 var 변수 선언을 하면 전역변수가 되기 때문에 전역을 오염시키지 않기 위해 IIFE패턴을 썼습니다.
```
// ES5
(function(){
	var a = 5;
})();
```

그러나 ES6에서 제공하는 let, const 선언은 지역변수이므로, 블록으로 묶어주기만 하면 IIFE패턴을 쓰지 않고도 전역을 오염시키지 않게 됩니다.
```
// ES6
{
	const a = 5;
	let b = 10;
}
```

아주 간단해졌습니다. :)


### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)

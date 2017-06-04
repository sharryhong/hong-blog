---
title: JavaScript ES6 문법 - rest parameter
date: 2017-02-26 22:55:00
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, rest parameter]
---

![JavaScript](/image/es6.png)

### rest parameter(나머지 파라미터 `...`)

일정하지 않은 갯수의 파라미터를 넘길 때 유용합니다.

```
function addNum(...numbers) {
  return numbers.reduce((sum, number) => {
    return sum + number;
  }, 0);
}

addNum(1,2,3,4,5);
```

arguments와 비교해보면 rest parameter의 장점이 드러납니다.

**ES5이하**

```
function arr() {
  console.log(arguments); // 유사배열인 [1,2,3,4,5,true,null,undefined]
  var arg = Array.prototype.slice.call(arguments, 2);
  console.log(arg); // [3,4,5,true,null,undefined]
}

arr(1,2,3,4,5,true,null,undefined);
```
이렇게 유사배열을 배열로 사용하려면 `Array.prototype.slice.call` 방식을 사용했습니다.

**ES6**

```
function arr(x , y, ...rest) {
  console.log(rest);
}

arr(1,2,3,4,5,true,null,undefined);
```
rest parameter방식을 사용하면 유사배열이 아닌 실제 배열로 반환합니다. `[3,4,5,true,null,undefined]`

### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)

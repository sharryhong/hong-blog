---
title: JavaScript ES6 문법 - Strings 문자열표기법 등
date: 2017-02-03 09:25:41
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, Strings]
---

![JavaScript](/image/es6.png)

## Template Strings

ES5에서 문자열을 변수, 함수와 함께 쓰고자 할 때 `+`기호를 씁니다.
```
let firstName = 'John';
let lastName = 'Smith';
const yearOfBirth = 1990;

function calcAge(year) {
	return 2017 - year;
}

// ES5
console.log('This is ' + firstName + ' '+ lastName +'. He was born in ' + yearOfBirth + '. Today, he is ' + calcAge(yearOfBirth) + ' years old.');
```
이처럼 때로는 번거롭게 코딩해야하는데요,

ES6에서는 `${value(변수, 함수 등)}`를 제공함으로서 보다 편리하게 코딩할 수 있습니다.
```
// ES6
console.log(`This is ${firstName} ${lastName}. He was born in ${yearOfBirth}. Today, he is ${calcAge(yearOfBirth)} years old.`);
```

### String 메소드들
```
const fullName = `${firstName} ${lastName}`;

console.log(fullName.startsWith('J')); 	// true
console.log(fullName.endsWith('th'));	// true
console.log(fullName.includes(' '));	// true
console.log(fullName.repeat(3));	// John SmithJohn SmithJohn Smith
console.log(`${fullName}, `.repeat(3));	// John Smith, John Smith, John Smith,
```

[String.prototype.startsWith()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)
특정 문자열로 시작하는지 확인하여 맞으면 true, 틀리면 false를 반환합니다.

[String.prototype.endsWith()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)
특정 문자열로 끝나는지 확인하여 맞으면 true, 틀리면 false를 반환합니다.

[String.prototype.includes()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
특정 문자열을 포함하고 있으면 true, 없으면 false를 반환합니다.

[String.prototype.repeat()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)
```
string.repeat(count);
```
count 횟수만큼 반복하여 문자열을 반환합니다.


### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)

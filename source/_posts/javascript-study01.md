---
title: 스터디그룹모임 - JavaScript 성능향상을 위한 노력, OOP(객체지향 프로그래밍)
date: 2017-01-20 17:47:16
categories: [Front-End, JavaScript]
tags: [JavaScript, 성능향상, callback]
---

![스터디그룹 홧팅!! ^^](/image/study_group.jpg)

> 스터디를 이어오고 있었는데 이제는 1주에 한번 서로 깨달은 점을 나누고,
궁금한 것은 공부해와서 다음에 나누기로 하였습니다.
이번주에 서로 나눈 내용은 JS성능향상을 위한 코드 리펙토링과 객체지향!

### 1. JavaScript 성능향상을 위한 고려

조건문의 경우 if else보다는 아닐경우 빠져나오는 경우를 먼저 설정하면 성능에 좋다고 합니다.
아래 예의 경우 항상 if가 참일 때는 A코드를, 아닐 경우는 B코드를 훑어봐야 합니다.
```
function addList(type, num){
	if( dbCheck(type, num) ){
		//...A
	} else { //...B }
}
```
이를 더 좋게 코드 리펙토링 한다면
```
function addList(type, num){
	if( !dbCheck(type, num) ){ return; }
	//...B
}
```
위처럼 아닐경우 빠져나가게(return) 설정한다면 모든 코드를 훑을 필요가 없어집니다.

### 2. 이벤트와 함수

아래처럼 이벤트가 실행될때 익명함수가 실행되게끔 하는 코드를 많이 사용하게 됩니다.

```
tar.addEventListener("focusout",function(evt){
	// do something
});
```

1) 이벤트와 함수를 분리하여 직관적으로 코드 리펙토링 해봅니다.
여기서 addText는 콜백함수이므로 focusout시 실행되므로 `()`를 적을 필요 없습니다.
```
function addText(evt){
  // do something
}

tar.addEventListener("focusout", addText);
```

2) 한번 더! 네임스페이스(전역에 하나의 객체만 추가하여 사용) 방식으로 코드 리펙토링
```
var addHandler = {
  'addText' = function() {
    // do something
  },
  'addNode' = function() {
    // do something
  },
  'addSomething' = function() {
    // do something
  },
}

tar.addEventListener("focusout", addHandler.addText);
```

### [3. OOP(Object Oriented Programming) 객체지향 프로그래밍 포스팅](https://sharryhong.github.io/2017/02/02/javascript-oop01/)

---
title: JavaScript - Module Patton
date: 2017-01-16 17:09:04
categories: [Front-End, JavaScript]
tags: [JavaScript, Module Patton, IIFE, Closure]
---

![JavaScript](/image/js.png)

> 이번에 진행할 Free Project에서 Module Patton으로 Module을 구현하려고 합니다.

**Module** : 모듈은 application's architecture(구조)의 필수 요소이며 일반적으로 프로젝트의 코드 단위를 명확하게 분리하고 구성하는 데 도움이됩니다.

자바스크립트에서는 모듈 구현을 위한 몇가지 방법이 있습니다.
The Module pattern (모듈패턴)
Object literal notation (객체 리터럴 표기법)
AMD modules
CommonJS modules
ECMAScript Harmony modules

## Module Patton(모듈 패텬)
모듈 패턴은 전통적인 소프트웨어 엔지니어링에서 클래스를 위한 private 및 public로 나뉜 캡슐화를 제공하는 방법입니다.

```
// data를 다루는 모듈
var budgetController = (function(){

	// private 영역
	// 클로저 내부에 있고 publicTest 메소드를 통해서만 엑세스가 가능하기 때문입니다.
	var x = 20; // private 프로퍼티
	var add = function(a){ // private 메소드
		return x + a;
	}

	// public 영역 : 필요한 것만 공개합니다.
	return {
		// 항상 x와 add에 엑세스하므로 클로저(closure)가 생성됩니다.
		publicTest: function(b){
			return add(b);
		}
	}
})();

// UI를 다루는 모듈
var UIController = (function(){
	// code
})();

// data와 UI를 같이 다루는 모듈
var controller = (function(budgetCtrl, UICtrl){
	var z = budgetCtrl.publicTest(5);

	return{
		anotherPublic: function(){
			console.log(z);
		}
	}
})(budgetController, UIController);
```

위 코드에서 public으로 공개된 코드를 사용하여 `controller.anotherPublic();` 이런식으로 budgetController의 publicTest 메소드에 접근합니다.

controller 내에서 `budgetCtrl.publicTest(5);`로 하지 않고, `budgetController.publicTest(5);`로도 접근이 가능하지만, 이 경우 나중에 budgetController의 이름을 바꾸게 된다면 모든 코드를 수정해야합니다.
따라서, 위처럼 매개변수로 받은 이름을 쓴다면 쉽게 수정이 가능해집니다.

### IIFE (Immediately Invoked Function Expressions 즉시실행함수)
```
(function(){
	// code
})();
```

위처럼 뒤에 `()`를 붙이면 함수가 즉시 실행됩니다.
함수내부 프로퍼티, 메소드는 외부에서 접근을 못한다는 개념을 사용하여 전역을 오염시키지 않도록 하는 방법입니다.

### 참고 자료
[Udemy - The Complete JavaScript Course](https://www.udemy.com/the-complete-javascript-course/learn/v4/overview)
[Nonblock 블로그](http://blog.javarouka.me/2012/02/javascripts-pattern-2-module-pattern.html)
[Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#modulepatternjavascript)

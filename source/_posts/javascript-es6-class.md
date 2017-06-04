---
title: JavaScript ES6 문법 - class
date: 2017-02-06 17:05:37
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, class]
---

![JavaScript](/image/es6.png)

## Class 클래스

자바스크립트 ES5 문법으로 class를 만들기 위해서 prototype 상속을 이용하는 방법을 사용하였습니다. [해당 포스팅 바로가기](https://sharryhong.github.io/2016/11/26/javascript-class/)
ES6 문법에서는 class 문법을 지원함으로서 이를 좀 더 쉽게 만들게 해줍니다.

#### ES5 와 ES6 비교

1_ ES5
```
// Person 클래스. 생성자 함수
var Person = function(name, yearofBirth, job) {
	// 프로퍼티
	this.name = name;
	this.yearofBirth = yearofBirth;
	this.job = job;
}
// 메소드
Person.prototype.calculateAge = function() {
	var age = new Date().getFullYear() - this.yearofBirth;
	console.log(age);
}
// 클래스 인스턴스
var john = new Person('John', 1980, 'teacher');
john.calculateAge();
```

2_ES6
```
// Person 클래스
class Person {
	// 생성자 메소드 : 초기 프로퍼티 설정
	constructor (name, yearofBirth, job) {
		// 프로퍼티   
		this.name = name;
		this.yearofBirth = yearofBirth;
		this.job = job;
	}
	// 메소드
	calculateAge() {
		let age = new Date().getFullYear() - this.yearofBirth;
		console.log(age);
	}
}

// 클래스 인스턴스
let john = new Person('John', 1980, 'teacher');
john.calculateAge();
```

static 메소드 : 클래스 인스턴스에 의해 상속되지 않는 메소드
```
// 클래스 내부에서
class Person {
	// static 메소드
	static greeting() {
		console.log('hi!');
	}
}

// 클래스 인스턴스
let john = new Person('John', 1980, 'teacher');

Person.greeting(); 	// 'hi!'
john.greeting(); 	// error
```

#### 특징

1) class 정의는 **호이스팅(hoisting) 되지 않습니다**. 따라서 클래스를 먼저 구현하고 사용해야합니다.

2) class에 메소드는 추가할 수 있지만 프로퍼티는 추가할 수 없습니다.
객체 인스턴스를 통해 상속된 프로퍼티는 좋은 코드가 아니기 때문에 문제가 되지 않습니다.

## 상속 구현
ES6, ES6모두 prototype 체인의 방법으로 상속이 구현됩니다.
ES6에서는 기존 객체지향 언어에서 제공하는 키워드인 class 등을 사용함으로써 좀 더 접근하기 쉬워졌습니다.

superclass(수퍼클래스, 부모클래스), subclass(서브클래스, 자식클래스)

1_ ES5

```
// 자식클래스
var Athlete = function(name, yearofBirth, job, olympics, medals) {
	Person.call(this, name, yearofBirth, job);
	this.olympics = olympics;
	this.medals = medals;
}

// 상속 구현 1) : Object.create() 사용하는 방법
Athlete.prototype = Object.create(Person.prototype);

// 상속 구현 2) : 자식클래스의 prototype에 부모클래스의 인스턴스를 대입하는 방법
Athlete.prototype = new Person();
Athlete.prototype.constructor = Athlete;

// 인스턴스
var johnAthlete = new Athlete('John', 1980, 'swimmer', 3, 10);

// 부모클래스의 메소드 사용
johnAthlete.calculateAge();
```

Person.call(this) : 부모클래스인 Person 생성자를 호출합니다.
[call() - MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

[상속 new와 Object.create](http://unikys.tistory.com/320)
[Object.create() - MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/create)


2_ ES6

```
// 자식클래스
class Athlete extends Person { // extends : 상속시 사용하는 키워드
	constructor(name, yearofBirth, job, olympics, medals) {
		// super : call the superclass. 부모의 생성자 호출
		super(name, yearofBirth, job);
		this.olympics = olympics;
		this.medals = medals;
	}
	// Athlete의 메소드
	wonMedal() {
		this.medals++;
		console.log(this.medals);
	}
}
// Athlete의 인스턴스
let johnAthlete = new Athlete('John', 1980, 'swimmer', 3, 10);
// 부모클래스의 메소드 사용
johnAthlete.calculateAge();
```

위와 같이 ES6에서 class, extends, super 등의 키워드를 제공함으로서 좀 더 편하게 상속 기능을 사용할 수 있습니다.

super(); = superclass.constructor()

#### 예제 추가 : Monster Game Class 만들기

> Monster 게임의 기본 클래스를 세팅해봅니다.
superclass는 Monster이며, 프로퍼티엔 name과 health(체력)이 있습니다.
체력은 100으로 초기화합니다. 생성자는 name 프로퍼티를 가진 option 객체로 호출됩니다.
subclass에 Snake 라는 클래스를 만듭니다. Snake에는 bite라는 기능(메소드)가 있습니다. 이 메소드의 유일한 인수(argument)는 Snake의 인스턴스입니다. (뱀이 뱀을 물다.) 물릴경우 체력이 -10 됩니다.

```
class Monster {
  constructor(options){
      this.name = options.name;
      // health는 100으로 초기화 되어있다.
      this.health = 100;
  }
}

class Snake extends Monster {
  // bite 메소드는 Snake class의 인스턴스를 매개변수로 받아
  // health값을 -10 한다.
  bite(snake) {
      return snake.health -= 10;
  }
}

let snake = new Snake({name: 'snakeya'});
snake; // {name: 'snakeya', health: 100}
snake.bite(snake); // 90 (snake.healt)
```


### 참고 자료
[Udemy - The Complete JavaScript Course](https://www.udemy.com/the-complete-javascript-course/learn/v4/overview)
[Udemy - ES6 Javascript: The Complete Developer's Guide](https://www.udemy.com/javascript-es6-tutorial)

### 연관 포스팅
[JavaScript Class (ES5)](https://sharryhong.github.io/2016/11/26/javascript-class/)

### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)

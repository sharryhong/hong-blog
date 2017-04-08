---
title: JavaScript 객체지향 - 캡슐화
date: 2017-02-06 14:54:18
categories: [Front-End, JavaScript]
tags: [JavaScript, 객체지향, 캡슐화]
---

{% asset_img oop.jpg [JavaScript OOP] %}

## 캡슐화 (encapsulation)
객체의 중요한 프로퍼티(데이터)와 메소드(기능)를 외부에서 접근하지 못하게 하는 작업을 말합니다. 

일반적으로 객체 내부의 프로퍼티, 메소드는 1)객체 내부, 2)객체 외부, 3)자식 객체에서 접근해 사용합니다. 

ES5 소스 예시
```
// MyParent 클래스
function MyParent() {
	this.property01 = 10; 
}
// 메소드 
MyParent.prototype.method01 = function() {
	this.property01 = 100;  // 1)객체 내부에서 접근 
}
// 인스턴스 생성
var my01 = new MyParent();
my01.method01(); 		// 2)객체 외부에서 접근 

// MyChild 클래스  
function MyChild() {
}
// 상속
MyChild.prototype = new MyParent();
MyChild.prototype.method02 = function() {
	this.method01(); 	// 3) 자식 객체에서 부모 메소드 접근 
}
```

객체지향 프로그래밍 에서 

| 접근 지정자 | 객체 내부 접근 | 객체 외부 접근 | 자식 객체 접근 |
| :----- |:-----:|:-----:|:-----:|
| public | O | O | O |
| protected | O | X | O |
| private | O | X | X |

자바스크립트 ES5에서는 위와 같은 접근지정자 문법을 지원하지 않기 때문에 아래와 같이 표현합니다. 
```
function MyClass() {

	// public 프로퍼티
	this.property01 = 10; 

	// private, protected 프로퍼티
	this._proterty02 = 20;
}

// public 메소드 
MyClass.prototype.method01 = function() {}

// private, protected 메소드
MyClass.prototype._method02 = function() {}
```

자바스크립트에서는 public만 지원하기 때문에 위와같이 약속하여 사용할 뿐, 객체 외부에서 접근이 가능합니다. 

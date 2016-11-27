---
title: javascript class (ES5)
date: 2016-11-26 22:18:00
categories: [Front-End, JavaScript]
tags: [JavaScript, Class, ES5, prototype]
---

{% asset_img js.png [JavaScript] %}

완전정복 스터디 3권(웹동네)으로 공부 + 코드 리펙토링 중 입니다. :) 
[해당 코드가 있는 Github 바로가기](https://github.com/sharryhong/TIL/tree/master/javaScript/02_class)

## Class 
함수가 특정 알고리즘을 포장하는 기술이라면, 클래스는 연관있는 변수와 함수만을 포장하는 기술입니다.
클래스로 포장하는 이유는 **객체 단위**로 코드를 그룹화 하고 **재사용**하기 위함입니다.

ES6에서는 *class*가 생겼지만 아직 이전 버전으로 개발을 많이 하고 있습니다. 

JavaScript에서 클래스처럼 사용할 수 있는 방법으로는
1. 리터럴 방식 
2. 함수 방식
3. 프로토타입 방식이 있는데 **프로토타입 방식을 선호**합니다. 
이유는 아래에 설명하겠습니다. 

### 개념 

##### 인스턴스 객체
함수를 사용하려면 함수호출을 해야하듯, 클래스를 사용하려면 일반적으로 인스턴스를 생성해야 합니다. 
클래스 : 설계도, 인스턴스 : 설계도대로 만들어진 결과물 


```
var 인스턴스 = new 클래스이름();
```

인스턴스가 만들어지면 클래스에서 포장해 놓은 프로퍼티와 메서드를 사용할 수 있게 됩니다. 

##### 프로퍼티 (변수)
주로 객체 내부에서 사용하는 일반적인 정보, 객체 내부 함수(메서드)에서 처리한 결과값 저장

##### 메서드 (함수)
주로 객체의 프로퍼티 값을 변경하거나 알아내는 기능, 클래스의 기능들 

##### 생성자
인스턴스가 만들어지면서 자동으로 호출되는 함수
생성자의 주 용도는 프로퍼티 초기화 역할 담당 

### 리터럴 방식으로 클래스 만들기 

```
var 인스턴스 = {
	프로퍼티: 초기 값 				// 프로퍼티 정의
	...
	메서드: function() {			// 메서드 정의
		...
	},
	...
}

// 객체 외부에서 접근하기 
인스턴스.프로퍼티;
인스턴스.메서드();
```

예 :  
```
$("p").css("color", "#f00");
```
$인 함수를 매개변수 값 "p"로 호출
$()함수에서 jQuery의 인스턴스를 만들어 리턴해주기 때문에 접근연산자 `.`를 이용해 jQuery가 제공하는 기능 중 css() 를 호출해 글자색을 변경할 수 있습니다. 

> **특징**
리터럴 방식에서는 **생성자가 존재하지 않습니다**.
리터럴 방식은 **클래스를 정의함과 동시에 자동으로 인스턴스가 만들어집니다**. 
단점 : **인스턴스를 하나만** 만들 수 있습니다.
주 용도 : 여러 개의 데이터를 묶어 값을 보관하거나 함수의 매개변수 값으로 전달할 때 주로 사용합니다. 

 ```
 var $ch = $("#ch");
 $ch.css({
 	"position": "absolute",
 	"top": 100,
 	"left": 100
 });
 ```

### 함수 방식으로 클래스 만들기 

```
// 일반 함수와 비교하기 위해 클래스이름은 대문자로 시작하도록 한다. (일반적인 규칙)
function 클래스이름() {
	this.프로퍼티 = 초기 값; 		// 프로퍼티 정의 
	...
	this.메서드 = function() { 	// 메서드 정의
	  ...
	}
	...
}

// 인스턴스 생성
var 인스턴스 = new 클래스이름(); 
// 메서드 호출
인스턴스.메서드();
```

> **특징**
생성자 : **클래스이름 자체가 생성자**이며 **인스턴스가 생성될 때 자동으로 호출**됩니다. 
장점 : **코드 재사용** 가능 
단점 : 인스턴스마다 **메서드가 중복해서 생성**됩니다. -> 치명적인 단점

### 프로토타입 방식으로 클래스 만들기 

클래스를 만드는 방법 중 가장 강력한 방법
jQuery도 프로토타입 방식으로 만들어졌다. 

```
function 클래스이름() {
	this.프로퍼티 = 초개 값;
	...
}

// 메서드는 prototype이라는 프로퍼티에 정의한다. 
클래스이름.prototype.메서드 = function() { 	
	...
}

// 인스턴스 생성
var 인스턴스 = new 클래스이름();
// 메서드 호출
인스턴스.메서드();
```

- 예 : [tabmenu_v02.js](https://github.com/sharryhong/TIL/blob/master/javaScript/02_class/js/tabmenu_v02.js)
```
// 2. 함수 단위 -> 프로토타입 방식 클래스 

(function(global, $){
'use strict';

// 인스턴스 생성 	
var tabTab1 = new TabMenu();
var tabTab2 = new TabMenu();

// 클래스 생성, 프로퍼티 생성 
function TabMenu() {
	this.$tab = null
	this.$tabMenus = null;
	this.$selectMenu = null;
}
// 메서드 생성, 요소 초기화  
TabMenu.prototype.init =function(el){
	this.$tab = $(el);
	this.$tabMenus = this.$tab.find('li');
	console.log(this);
}

TabMenu.prototype.initEvent = function(){
	var objThis = this;		// 아래에 설명 추가 
	this.$tabMenus.on("click", function(){
		objThis.setSelectMenu($(this));
	});
}

TabMenu.prototype.setSelectMenu = function($thisMenu){
	if(this.$selectMenu){
		this.$selectMenu.removeClass('select');
	}
	this.$selectMenu = $thisMenu;
	this.$selectMenu.addClass('select');
}

tabTab1.init('#tabMenu1');
tabTab1.initEvent();

tabTab2.init('#tabMenu2');
tabTab2.initEvent();

})(this, this.jQuery);
```

 - 클릭(이벤트) 전 `this` 는 아래처럼 구성되어 있다. (크롬 개발자도구)

 ```
 TabMenu
		$selectMenu:null
		$tab:n.fn.init[1]
		$tabMenus:n.fn.init[6]
		__proto__: Object
		constructor:TabMenu()
		init: function(el)
		initEvent: function()
		setSelectMenu: function($thisMenu)
		__proto__: Object

 ```

> **특징**
**코드 재사용**
모든 인스턴스는 **prototype**에 만들어져 있는 **메서드를 공유해서 사용**합니다. 
자바스크립트에서는 prototype을 이용해 **상속을 구현**합니다. 

```
TabMenu.prototype.initEvent = function(){
	var objThis = this;
	this.$tabMenus.on("click", function(){
		objThis.setSelectMenu($(this));
	});
}
```
 위 코드에서  `this.$tabMenus.on("click",...` 클릭을 하면 `this`가 **클릭한 li요소**로 되어버립니다. <br>
 따라서 변수 objThis에 본래의 this를 저장하여 `objThis.setSelectMenu($(this));`로 사용한 것입니다. 

### 연관 사이트 
[MDN - JavaScript Class (ES6)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes)

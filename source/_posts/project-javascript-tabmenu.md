---
title: JavaScript TabMenu (ES5_prototype class)
date: 2016-11-28 13:16:12
categories: [Portfolio, Free Project]
tags: [JavaScript, Class, ES5, prototype, TabMenu]
---

### JavaScript 프로토타입 방식으로 클래스 만들기 - 탭 메뉴

![결과 이미지](/image/tabmenu.jpg)

[해당 코드가 있는 Github 바로가기](https://github.com/sharryhong/FDS/blob/master/day06_css/css/file-format-icons03.css) | [결과화면 보기](https://sharryhong.github.io/TIL/javaScript/02_class/tabmenu.html)

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

####  `this`에 대하여

클릭(이벤트) 전 `this` 는 아래처럼 구성되어 있습니다. (크롬 개발자도구)
클래스에 프로퍼티와, prototype에 메서드가 정의되어 있는 걸 볼 수 있습니다.

```
 TabMenu
		$selectMenu:null
		$tab:n.fn.init[1]
		$tabMenus:n.fn.init[6]
		__proto__: Object		// = prototype
		constructor:TabMenu()
		init: function(el)
		initEvent: function()
		setSelectMenu: function($thisMenu)
		__proto__: Object

```


```
TabMenu.prototype.initEvent = function(){
	var objThis = this;
	this.$tabMenus.on("click", function(){
		objThis.setSelectMenu($(this));
	});
}
```
위 코드에서  `this.$tabMenus.on("click",...` 클릭을 하면 `this`가 **클릭한 li요소**로 되어버립니다.
(이벤트에서 this는 이벤트를 발생시킨 객체이기 때문입니다.)
따라서 변수 objThis에 본래의 this를 저장하여 `objThis.setSelectMenu($(this));`로 사용한 것입니다.

### 연관 링크
[JavaScript ES5 Class - 관련 링크 바로가기](https://sharryhong.github.io/2016/11/26/javascript-class/)

---
title: javascript class (ES6)
date: 2016-11-26 23:04:19
categories: [Front-End, JavaScript]
tags: [JavaScript, Class, ES6]
---
{% asset_img js.png [JavaScript ES6] %}

업뎃중 ^^

```
class Polygon {  // 클래스 이름
  constructor(height, width) {  // 생성자 (클래스가 만들어지면서 생성자 자동실행)
    this.height = height;		// 초기화
    this.width = width;
  }
}
```

```
var p = new Polygon(); // ReferenceError 호이스팅이 안되므로 에러 

class Polygon {}
```
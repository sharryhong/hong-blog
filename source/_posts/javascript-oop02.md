---
title: JavaScript 객체지향 - 추상화
date: 2017-02-05 13:43:15
categories: [Front-End, JavaScript]
tags: [JavaScript, 객체지향, 추상화]
---

![JavaScript OOP](/image/oop.jpg)

## 추상화 (abstraction)
객체의 **프로퍼티와 메소드를 정의** 하는 작업으로, 이름을 작성하는 선언 부분만 만들 뿐 구현부분은 작업하지 않습니다.

자바스크립트에서는 인터페이스와 추상클래스를 제공하지 않기 때문에 클래스만을 이용해서 추상화 작업을 해야합니다.

#### 예: 이미지 슬라이더 추상화 하기

| ImgSlider 프로퍼티 |
| :----- |
| 현재 선택된 이미지 인덱스 |
| 이미지 목록 |

| ImgSlider 메소드 |
| :----- |
| 자동 플레이 기능 시작 |
| 자동 플레이 기능 멈춤 |
| 다음 이미지 이동 |
| 이전 이미지 이동 |
| index번째 이미지 이동 |

위를 소스로 표현하면 (ES5)
```
function ImgSlider(selector) {
	this.selectIndex;
	this.imgList;
}
ImgSlider.prototype.startAutoPlay = function() {}
ImgSlider.prototype.stopAutoPlay = function() {}
ImgSlider.prototype.nextImg = function() {}
ImgSlider.prototype.prevImg = function() {}
ImgSlider.prototype.setImgAt = function(index) {}
```


### 참고 자료
웹 프론트엔드 개발자를 위한, 자바스크립트+jQuery 완전정복 스터디 - 김춘경(딴동네)

## 관련 포스팅
[객체지향 프로그래밍 개념](https://sharryhong.github.io/2017/02/02/javascript-oop01/)

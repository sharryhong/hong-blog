---
title: 스터디그룹모임 - JavaScript의 this 
date: 2017-02-12 18:07:05
categories: [Front-End, JavaScript]
tags: [JavaScript, this]
---

{% asset_img study_group.jpg [스터디그룹 홧팅!! ^^] %}

> 이번주에 우리 스터디모임에서 나눈 주제는 크로스브라우징, JS ES6 - Arrow Function, 원시데이터와 참조데이터였습니다. 
Arrow Function에 대해서는 제가 발표자였는데, **JavaScript의 this**에 대해 좀 더 자세하게 다뤄야할 필요성이 느껴지더라고요. 잘 알고있다고 생각했는데 클래스, 인스턴스, 메소드 등의 this에 대해서 정리가 필요할 것 같았습니다. 

## this란?
일반적으로 메소드를 호출한 객체가 저장되어 있는 속성입니다. 
하지만 JavaScript의 this 속성은 메소드를 호출할 때 뿐 아니라, 일반 함수를 호출할 때, 이벤트 리스너가 호출될 때, 중첩 함수에서 등에서의 this가 달라지게 됩니다. 
간단하게 표로 나타내면.. 

| this가 만들어지는 경우 | this 값 | 
| :----- | :----- |
| 1_일반 함수 | window |
| 2_중첩 함수 | window |
| 3_이벤트 | 이벤트를 발생시킨 객체 |
| 4_메소드 | 메소드를 호출한 객체 |
| 5_메소드 내부의 중첩함수 | window |

### 1_일반 함수에서의 this


### 참고 자료
웹 프론트엔드 개발자를 위한, 자바스크립트+jQuery 완전정복 스터디 - 김춘경(딴동네) 
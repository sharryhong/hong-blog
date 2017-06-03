---
title: Web DOM API - Element
date: 2017-01-07 15:10:20
categories: [Front-End, DOM API]
tags: [JavaScript, DOM, Web API - Element]
---

{% asset_img dom.png [DOM] %}

>  Free Project를 진행하면서 자주 사용하는 Element Web API를 계속 추가할 예정입니다. :)

## [element.classList](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)
요소의 class속성 목록을 반환합니다.

###### 브라우저 호환 : IE10이상

**add** : 요소의 클래스 목록에 클래스 추가
**remove** : 요소의 클래스 목록에서 클래스 삭제
**toggle** : 요소의 클래스 목록에서 특정 클래스 전환
**contains** : 요소의 클래스 목록이 특정 클래스를 포함 여부 확인

**classList를 지원하는지 확인**하고 class속성에서 no-js값을 js로 변경하는 코드
```
(function(global){
  'use strict';

  // <html> 요소를 찾아서 class 속성에서 'no-js' 값을 'js'로 변경
  global.html = query('html');

  if ( html.classList ) {
    // 신형 방식 IE 10+
    html.classList.remove('no-js');
    html.classList.add('js');
  } else {
    // 구형 방식
    var html_class_attr = html.getAttribute('class');
    // 설정
    html.setAttribute('class', html_class_attr.replace(/no-js/,'js'));
  }

}(this));
```

### 관련 My 포스팅
[JavaScript DOM](https://sharryhong.github.io/2016/12/28/javascript-dom/)

### 참고 자료
[Web APIs Element - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Element)

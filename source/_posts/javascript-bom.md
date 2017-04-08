---
title: JavaScript BOM
date: 2016-12-28 18:06:59
categories: [Front-End, JavaScript]
tags: [JavaScript, BOM]
---

{% asset_img bom.jpg [JavaScript BOM] %}

> JavaScript를 배운다는 건...  
core(문법), core library(기본 제공 함수 등), BOM, DOM 
이 중 BOM에 대해 정리해보겠습니다. 

## BOM(Brower Object Model)
웹 브라우저를 구성하는 객체들이 포함되어 있습니다. 

#### Window 객체 
Javascript 실행시 가장 상위에 존재하는 객체입니다.
웹 페이지의 정보에 접근하거나 변경을 할 수 있습니다.
윈도우 창을 구성하며 server-side에는 없습니다. 
브라우저별로 문법이 다르기 때문에 크로스브라우징이 어렵습니다. 
IE9부터는 표준을 지켜서 괜찮으나 IE8은 고려해야 합니다.

**Navigator**		: 브라우저 정보
**Location**		: 주소창 부분
**History**		: 이번보기 다음보기 등
**Document**		: 웹 페이지 문서의 HTML, CSS 등에 대한 접근 가능. 가장 중요한 개념 
**Screen** 		: 디스플레이 부분

※크롬 콘솔창에 `window`라고 치면 window 객체에 내장되어 있는 프로퍼티들이 쭉 나옵니다. 
※ `wondow.`은 생략이 가능합니다. 

#### 주요 프로퍼티 등
`window.devicePixelRatio` : 기기의 픽셀 농도
`window.innerWidth` : window의 화면 가로 폭
`window.innerHeight` : window의 화면 세로 폭
`window.alert("Dialog 창 띄우기");` : 오늘날은 alert창 별로 쓰지 않고 console로 씁니다.
`window.prompt('당신의 이름은?', '예) 홍길동');` : 입력창이 뜹니다. 잘 쓰지 않습니다. 
`window.confirm("당신은 청년입니까?");` : Yes, No 값을 받을 수 있습니다.
`window.open('http://www.naver.com');` : 들어가자마자 새창이 뜹니다. 요샌 쓰지 않습니다. 
`window.scrollX` = `window.pageXOffset;` : 가로 스크롤바 위치
`window.scrollY` =` window.pageYOffset` : 세로 스크롤바 위치 (나중에 스크롤 moving사용시 씀)
크롬은 둘다 사용. 브라우저별로 다른 문법 사용
`window.scrollTo(0,1000);` : x축 0, y축 1000px 절대적 위치이동
`window.scrollBy(0,100);` : x축 0, y축 1000px 상대적 위치이동
`window.setInterval(할일(함수), 시간(밀리초));` : 주기마다 계속 함수 반복
`window.setTimeout(할일(함수), 시간(밀리초));` : 시간 후에 1회만 함수 실행
`window.clearInterval()` : 멈춤. 변수에 setInterval되는 것을 담아놨다가 ()안에 넣기
`window.requestAnimationFrame();` : setInterval의 단점을 보완. IE10부터.

#### Location (주소창) 객체

`location.href;` : 주소 "http://caniuse.com"
`location.protocol;` : "http:"
`location.domain;`
`location.host;` : "caniuse.com"
`location.hostname;` : "caniuse.com"
`location.port;`
`location.hash;` : 해당페이지의 목적지(id)

#### History 객체

`history.back()` : 한칸 뒤로가기
`history.forward()` : 한칸 앞페이지 가기
`history.go(-2)` : 2칸 뒤로가기 등 제어가능

#### Screen 객체

정확하게 말하자면 내 노트북의 모니터 screen 정보를 말하는 것입니다.
통계할 때 빼곤 잘 쓰지 않습니다.
`screen.width` : 스크린 width
`screen.height` : 스크린 height
`screen.availHeight` : 실제 사용가능한 height
`screen.orientation` : 중요! 모바일 등 제어 
```
// 기울기, 가로모드, onchange되면.. 설정가능
ScreenOrientation {angle: 0, type: "landscape-primary", onchange: null}` 
```
예 )
```
screen.orientation.onchange = fnction() {
  if ( screen.orientation.type == 'landscape-primary') {
  ... 
  }
}
```

#### Navigator 객체

`navigator.userAgent` : 사용자의 브라우저 식발자를 감지하여 거기에 맞는 디자인이 가능합니다. 
: 크롬 개발자도구의 모바일 버전으로 테스트가 가능합니다.
"Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/51.0.2704.103 Safari/537.36"
`navigator.appCodeName ` : "Mozilla"
`navigator.userAgent.indexOf('Chrome') > -1;` : Chrome이라는게 있니? 즉, 크롬이니?. 해당 문구가 없다면 -1이 나옵니다. -1보다 크다면(크롬이라면) true를 반환합니다.
`navigator.vendor` : 크롬 웹브라우저의 경우 "Google Inc."
`navigator.cookieEnabled` : 쿠키를 쓸 수 있나? true. 현재 모든 브라우저는 쿠키 쓸 수 있습니다.
`!!window.localStorage` : 새로운 기술. 로컬스토리지
`navigator.onLine` : 온라인인가? true : 온라인일 때 다운받게 하기 등 가능
`navigator.language` : 주 언어 "ko"

#### Document 객체 
웹 페이지 문서의 HTML, CSS 등에 대한 접근을 가능하게 하므로 Front-End개발에서 가장 중요한 개념입니다. 

`document.title` : title
`document.doctype` : <!DOCTYPE html>
`document.compatMode` : "CSS1Compat" 표준모드. "BackcCompat" 비표준모드
`돔스크립트(DOM Script)` : 자바스크립트를 사용한 문서 동적 제어
```
// 웹 표준 호환 모드라면 standard_mode에 true값이 참조(Reference)됩니다.
var standard_mode = document.compatMode == 'CSS1Compat';
// 문서에서 root element인 <html> 요소를 찾아서 변수 html에 참조됩니다.
var html = document.documentElement;
// 웹 표준 호환 모드라면 첫번째 코드 블록문이 실행
if ( standard_mode ) {
  // 변수 html에 참조된 문서 객체 <html>요소에 class 속성 값을 'standard'로 설정합니다. 
  html.setAttribute('class', 'standard');
} else {
  html.setAttribute('class', 'nostandard');
}
```
`document.activeElement;` : focus된, 활성화된 엘리먼트를 알 수 있습니다. 접근성에서 중요합니다.
`document.write('');` : html코드에 추가되는데 이젠 이렇게 잘 쓰지 않습니다.

[DOM에 대한 포스팅 바로가기](https://sharryhong.github.io/2016/12/28/javascript-dom/)
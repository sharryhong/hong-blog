---
title: Networking - AJAX 비동기 통신 기술
date: 2016-12-29 18:31:02
categories: [Front-End, AJAX]
tags: [JavaScript, AJAX, JSON]
---

{% asset_img ajax.png [AJAX 기술] %}

## AJAX(Asynchronous Javascript And XML) 개념
Javascript가 XML을 만나면서 비동기 통신을 한다. -> 요새는 XML보다는 JSON으로 하지만 이름은 그대로 사용하고 있다고 하네요. ^^
XML은 자유롭게 마음대로 정할 수 있지만 무겁고 구조화가 어렵다는 단점이 있습니다. 이를 해결하기위해 JSON 등장!

**비동기 통신** : view가 update하는 동안에도(data 변경 등) 사용자는 다른 일을 할 수 있습니다. 자바스크립트 객체가 특정 데이터(업데이트 등을 할 데이터)를 서버에 주고받고 하여 그 부분만 업데이트합니다.
**필요한 부분만 별도로 요청, 응답받아 처리**합니다. 모든데이터를 업데이트할 필요없어 **불필요한 대역폭 감소**가 가능하고 **비용절감**을 가져옵니다.

장점 : 사용자에게 더 나은 사용 경험 제공. 속도, 비용 절감
단점 : 접근성에는 열악합니다. -> 해결하기 위해 등장 : [WAI-ARIA](https://sharryhong.github.io/2016/12/13/web-aria/)

### AJAX 기술
브라우저에서 페이지를 이동하지 않고 자바스크립트를 통해 HTTP Request를 보내고 받아 JS에서 처리할 수 있습니다.


서버 설치 : `$ npm install http-server -g`
로컬 서버 연결 : `$ http-server -o -a localhost -p 8081`
: `http://localhost:8081`로 자동으로 띄워줍니다.

1) create. **XHR**(XML Http Request)
AJAX 통신을 하기 위한 생성자를 통해 객체를 만듭니다. 여러개를 만들어 동시다발적으로 수행시킬 수 있습니다.
```
var xhr = new XMLHttpRequest();
```

2) open 메소드 : setting 구간. 요청의 방식과 url설정
```
xhr.open('GET', 'data/data.json');
```

3) send 메소드 : 요청 전송. 통신 시작
```
xhr.send();
```

응답확인 : `xhr.response` 콘솔창에 쳐보면 data.json 데이터를 볼 수 있습니다.

#### XMLHttpRequest에서 http요청을 보냈을 때 발생하는 이벤트의 종류
##### readyState 속성
AJAX 요청에 따라 0~4까지 변화
0 : open 메소드 호출 전
1 : open 메소드 호출 후
2 : 보낸 요청에 대해 응답 헤더가 수신된 후
3 : 응답의 바디 부분이 수신중일 때
**4 : 모든 응답이 수신되었을 때**

##### status 속성
HTTP response의 응답 헤더에 기록된 코드
**200 : OK. 정상적으로 data를 보냄**
404 : Not Found
500 : Internal Error

##### onreadystatechange 속성
readyState가 변할 때마다 호출되는 콜백 함수

```
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function a() {
	console.log(this.readyState, this.status);
	if(this.readyState == 4 && this.status == 200) {
		console.log(this.response);
	}
}
xhr.open('GET', './data.txt');
xhr.send();
```

## JSON (JavaScript Object Notation)
AJAX 형태로 받은 문자를 객체로, 객체를 문자로 바꿀 수 있는 능력을 가지고 있습니다.
**자바스크립트 객체를 문자열로 표현**하므로 프로그램간에 전달하기 편리합니다.
서버에서 보낼 데이터를 JSON형태로 브라우저로 전송
데이터를 수신한 브라우저는 자바스크립트를 통해 데이터를 파싱하고 문서에 반영합니다.

#### JSON API
`JSON.stringify(object)` 메소드 : 인자로 받은 객체를 JSON 문자열로 반환
`JSON.parse(string)` 메소드 : 인자로 받은 문자열을 Javascript Object로 변경하여 반환
※ undefined, function 은 변환되지 않습니다.



### 참고 자료
[helloworld - 자바스크립트와 웹 프론트엔드](http://tryhelloworld.co.kr/courses/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%99%80-%EC%9B%B9-%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C)
[My Github 링크](https://github.com/sharryhong/FDS/tree/master/day41-angulerjs)

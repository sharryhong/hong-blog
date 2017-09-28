---
title: HTTP(Hyper-Text Transfer Protocol)
date: 2017-09-27 12:18:39
categories: [plus forWeb!, Computer Science]
tags: [HTTP, Protocol]
---

![HTTP](/image/http.png)

### 프로토콜(Protocol))이란?
데이터를 어떤 형태로 주고 받을 것인지 정한 규약

## HTTP(Hyper-Text Transfer Protocol)란?
웹서버(HTTP Server)와 웹브라우저(HTTP Client) 사이에 데이터를 주고 받는 형식
즉 인터넷 상에서 데이터를 어떻게 주고 받는지를 정의해 둔 것으로 모든 웹브라우저가 이 방식을 따릅니다.

### HTTP Request(요청) 형식
```
Request-Line CRLF
((general header | request header | entity header) CRLF)*
CRLF
message-body
```
**1) Request-Line CRLF**
  - 요청 대상을 가리키는 한 줄 문자열을 보낸다.
  - 문법 - 요청형식 공백 요청URI 공백 프로토콜버전 줄바꿈
  예) GET /pub/WWW/TheProject.html HTTP/1.1 (CRLF)
  - **요청 형식**
  **GET** : 자원 조회를 요청할 때 사용한다.
  **POST** : 자원의 추가, 변경을 요청할 때 사용한다.
  **HEAD** : 생성일, 크기 등 자원의 정보만 요청할 때 사용한다.
  **PUT** : 자원 추가를 요청할 때 사용한다.
  **DELETE** : 자원 제거를 요청할 때 사용한다.
  기타 OPTIONS, TRACE, CONNECT 등이 있다.

**2) 헤더 정보**
  - 요청에 대한 부가 설명을 담은 데이터이다.
  - 3가지 종류의 데이터로 구성된다.
  일반정보(general header) : 요청과 응답에 모두 사용되는 데이터
  요청정보(request header) : 요청할 때만 전달하는 데이터
  엔티티정보(entity header) : 보내는 데이터에 대한 정보. 단 POST 요청일 때만 보낸다.
  - 문법 - 헤더명: 값 CRLF
  예) Host: www.w3.org

**3) message-body**
  - GET 요청에는 message-body가 없다.
  - POST 요청일 때 message-body가 추가된다.
  - 문법 - 이름=값&이름=값&이름=값
  예) pageNo=1&pageSize=6&align=desc

### HTTP Response(응답) 형식
```
Status-Line CRLF
((general header | response header | entity header) CRLF)*
CRLF
message-body
```
**1) Status-Line CRLF**
  - 응답 상태 정보를 표현하는 문자열 한 줄
  - 문법 - 프로토콜버전 공백 상태코드 공백 간단한설명 (CRLF)
  - 예) HTTP/1.1 200 OK
  - 주요 **상태 코드**와 의미
  200 : 요청한 자원을 줄 수 있다.
  301 : 요청한 자원의 주소가 바뀌었다. 다시 요청하라!
  304 : 요청한 자원이 변경되지 않았다.
  그러니 웹브라우저가 캐시한 자원을 그냥 사용하라!
  400 : 요청 형식에 문제가 있다. 올바르게 요청하라!
  403 : 해당 자원에 대한 요청을 거절한다.
  404 : 요청한 자원을 못 찾았다.

**2) 헤더 정보**
  - 응답에 대한 부가 설명을 담은 데이터이다.
  - 3가지 종류의 데이터로 구성된다.
  일반정보(general header) : 요청과 응답에 모두 사용되는 데이터
  응답정보(request header) : 응답할 때만 전달하는 데이터
  엔티티정보(entity header) : 응답 데이터에 대한 정보.
  - 문법 - 헤더명: 값 CRLF
  예) Server: Apache

**3) message-body**
  - 웹서버가 웹브라우저에게 응답하는 데이터
  - 보통 HTML이 리턴된다.
  - HTML 외에도 JSON, XML, Plain Text, gif 등 텍스트 데이터에서 바이너리 데이터까지
  다양한 데이터를 리턴할 수 있다.



**잘 정리되어 있는 사이트**
[HTTP 그리고 REST API 다가가기](http://jinbroing.tistory.com/96)

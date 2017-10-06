---
title: REST, RESTful API
date: 2017-09-30 14:54:47
categories: [Back-End, 기타]
tags: [RESTful]
---

![RESTful API](/image/restful.png)

## REST(Representational State Transfer)
네트워크 아키텍처 원리의 모음
웹 리소스(자원)를 요청해서 받고 서버에 올릴 때 어떻게 전송, 요청을 할 것인가..
데이터를 주고 받을 때 필요한 스타일, 패턴

## RESTful API
REST를 잘 준수한 API
- HTTP Protocol 기반
- 리소스는 URI로 표현하며 고유해야한다.
- URI는 단순하고 직관적인 구조여야한다.
- 리소스의 상태는 GET, POST, PUT, DELETE 등 HTTP Method를 활용해서 구분한다.
- 주로 JSON을 활용하여 데이터를 전송한다.

#### URI 설계
- 소문자 사용(대소문자 구분)
- 경로에 공백대신 하이픈(-)을 사용한다. 밑줄은 링크때문에 가려질 수 있다.
- 확장자를 사용하지 말자.
- CRUD는 URI에 사용하지 않는다(예: /delete?id=2). HTTP Method를 사용하여 처리한다.
- 주로 복수명사 사용 (예: /movies)
- 필요시 URL에 하위 자원을 표현 (예: /movies/20)
- 필터조건을 허용할 수 있다 (예: /movies?state=active)


**참고 자료**
[위키피디아-REST](https://ko.wikipedia.org/wiki/REST)
[inflearn-Node.js](https://www.inflearn.com/course/node-js-%EC%9B%B9%EA%B0%9C%EB%B0%9C/)
[RESTFul이란 무엇인가?](http://blog.remotty.com/blog/2014/01/28/lets-study-rest/)

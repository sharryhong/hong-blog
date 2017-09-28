---
title: TCP와 HTTP
date: 2017-09-27 14:41:38
categories: [plus forWeb!, Computer Science]
tags: [HTTP, TCP]
---

![OSI 7 계층 모형](/image/osi.jpg)

### TCP(Transmission Control Protocol)
전송 계층(Transport layer)에 위치한다.
네트워크의 정보 전달을 통제하는 프로토콜이자 인터넷을 이루는 핵심 프로토콜의 하나
웹 브라우저들이 월드 와이드 웹에서 서버에 연결할 때 사용되며, 이메일 전송이나 파일 전송에도 사용된다.
근거리 통신망이나 인트라넷, 인터넷에 연결된 컴퓨터에서 실행되는 프로그램 간에 일련의 옥텟을 안정적으로, 순서대로, 에러없이 교환할 수 있게 한다.

- Transport layer
계층 구조의 네트워크 구성요소와 프로토콜 내에서 송신자와 수신자를 연결하는 통신 서비스를 제공한다.
연결 지향 데이터 스트림 지원, 신뢰성, 흐름 제어, 그리고 다중화와 같은 편리한 서비스를 제공한다.

### [HTTP(Hyper-Text Transfer Protocol) : 포스팅 참고](https://sharryhong.github.io/2017/09/27/back-protocol/)
응용 계층(Application layer)에 위치한다.
기반이 되는 전송 계층(Transport layer) 프로토콜을 사용하여 호스트 간 연결을 확립한다.

개념적으로 살펴 보면 HTTP, HTTPS, FTP 등의 프로토콜은 TCP/IP 위에서 동작한다고 볼수있다.

**데이터 형태**
tcp : byte array(binary)로 정보를 통신
http: String으로 정보를 통신

**연결방식**
tcp : 언제나 서버와 연결되어있어야하며, request 없이도 recevie가 일어난다.
http: keep-alive로 지속적인 연결은 가능하지만 기본적으론 close로 되어 있으며, request를 하여야만 recevie가 일어난다.


#### 참고 사이트
[위키피디아-TCP](https://ko.wikipedia.org/wiki/%EC%A0%84%EC%86%A1_%EC%A0%9C%EC%96%B4_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
[위키피디아-OSI 7 계층 모형](https://ko.wikipedia.org/wiki/OSI_%EB%AA%A8%ED%98%95)
[tcp/ip와 http의 차이](http://blog.naver.com/PostView.nhn?blogId=k220j&logNo=220694238797)

---
title: 02. URL Routing 처리하기
date: 2017-10-06 18:18:21
categories: [Back-End, Nodejs]
tags: [node.js, express, Routing]
---

![Node.js](/image/nodejs.png)

**[라우팅(Routing)이란?](https://ko.wikipedia.org/wiki/%EB%9D%BC%EC%9A%B0%ED%8C%85)**
네트워크 안에서 통신 데이터를 보낼 **경로**를 선택하는 과정


### GET 요청 처리
```
app.get('/', function(req, res) { // url path, 콜백함수
  res.sendFile(__dirname + "/public/main.html")
})
```
- 비동기로 처리됩니다.
- 절대경로를 적어줘야합니다. node에서 제공해주는 `__dirname` : 현재까지의 경로
- root로 접속했을 때 public 폴더에 main.html 파일을 클라이언트에 보내줍니다.


**관련 포스팅**
[GET과 POST 요청](https://sharryhong.github.io/2017/10/06/back-get-post/)

**참고 자료**
[인프런 Node.js강의](https://www.inflearn.com/course/node-js-%EC%9B%B9%EA%B0%9C%EB%B0%9C/)

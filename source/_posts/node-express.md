---
title: Express 모듈로 간단하게 웹 서버 만들기
date: 2017-09-30 17:39:35
categories: [Back-End, Nodejs]
tags: [node.js, express, nodemon]
---

## 익스프레스(Express)
Node.js에 기본으로 있는 http모듈을 사용하면 웹 서버 기능을 담당하는 서버 객체를 만들 수 있습니다.
하지만 http 모듈만 사용해서 웹 서버를 구성할 때는 많은 것들을 직접 만들어야 합니다.
**Express는 좀 더 쉽고 빠르게 웹 서버를 구성**하도록 코드를 자동으로 만들어 줍니다.

### **1_ 익스프레스 모듈 설치**
```
$npm install express --save
```
`--save`를 하면 package.json파일의 dependencies에 추가됩니다.

### **2_ 웹 서버 만들기 기본 (app.js)**
```
var express = require('express')   // express 모듈 불러오기
var app = express()                // 반환값이 함수이기 때문
app.listen(3000, function() {      
  console.log('start!  express server on port 3000')
})
```
실행
```
$node app.js
```
결과
- listen함수 실행 : 3000포트 기반으로 콜백함수를 실행하고, 응답을 받기 위한 대기 상태가 됩니다.
- http://localhost:3000/ 로 정상적으로 서버에 접속됩니다.
- 콜백함수는 비동기로 동작하기 때문에 스택에 쌓였다가 서버에 접속하면 실행됩니다.

### **3_ nodemon 모듈로 간편하게 사용하기**
app.js 파일을 수정하면 서버를 껐다 켜야합니다.
nodemon모듈을 설치하면 자동으로 파일의 변화를 감지하여 노드 서버가 재실행 하도록 해줍니다.

global에 nodemon 설치
```
$npm install nodemon -g
```
실행
```
$nodemon app.js
```
이제 app.js를 수정하면 자동으로 서버를 재실행되어 편리합니다. 

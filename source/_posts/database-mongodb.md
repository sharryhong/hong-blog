---
title: MongoDB Window 설치
date: 2017-03-03 23:32:03
categories: [Back-End, Database]
tags: [MongoDB]
---

{% asset_img logo.png [MongoDB] %}

> React 스터디를 진행하면서 윈도우유저들은 몽고디비를 먼저 설치해보라는 명이 떨어졌습니다. ㅋㅋ
왜 맥에서는 쉽게 설치가 되는 것들이 윈도우에서는 약간?의 말썽이 일어나는 것일까요. 크~
도움받은 사이트와 진행을 쉽게 정리해보고자 합니다.

1_ 설치 ([참고사이트](http://cyberx.tistory.com/76))

[mondodb.com](https://www.mongodb.com/download-center#community) 에서 msi파일을 다운로드 받습니다.
저는 첫번째인 `Windows Server 2008 R2 64-bit and later, with SSL support x64` 를 다운받았습니다.

msi파일을 실행하면 잘 설치됩니다. 저의 경우 `C:\Program Files\MongoDB\Server\3.4\bin`의 경로에 설치되었습니다.

2_ 환경변수 등록 ([참고사이트](http://7stocks.tistory.com/7))

`제어판` -> `시스템 및 보안` -> `시스템`에서 `고급 시스템 설정` 탭 -> `환경 변수`를 클릭합니다.

`새로 만들기` 클릭
```
변수이름 : MONGODB_HOME
변수 값 : C:\Program Files\MongoDB\Server\3.4
```

3_ DB가 저장되는 기본폴더를 만들어줍니다.

cmd를 실행시키고, `mkdir c:\data\db` 로 폴더를 만들어줍니다.

4_ MongoDB 서버를 실행합니다.

cmd에서 `"C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe"`

서버가 실행됩니다.

5_ MongoDB가 잘 동작하는지 확인합니다.

cmd에서 `"C:\Program Files\MongoDB\Server\3.4\bin\mongo.exe"`

test 데이터베이스에 연결됩니다.

---
title: Firebase - Realtime Database
date: 2017-01-25 13:55:09
categories: [Back-End, Database]
tags: [Firebase, Realtime Database]
---

![Firebase](/image/firebase.png)

## [Firebase on the Web - Firecasts Youtube](https://www.youtube.com/playlist?list=PLl-K7zZEsYLmnJ_FpMOZgyg6XcIGBu2OX)

> 실제 데이터를 구현하고 싶은 욕망이 항상 있었는데, 이번 예산관리 웹앱을 만들면서 파이어베이스로 디비구현 및 실제 데이터를 붙여보고 싶었습니다.
파이어베이스가 스타트업으로 시작해서 구글에서 인수했다고 들었는데.. 능력자들!

#### firebase로 할 수 있는 것들 (web기준)
- 인증, 스토리지, 호스팅, firebase 클라우드의 웹푸시 알림 등
- Angular 1 & 2, Polymer, React, Ember등의 자바스크립트 프레임워크 연동

## Realtime Database - 간단하게 구현해보기

#### Firebase 시작!
1. <https://firebase.google.com> 간단하게 가입 후 무료로 시작하기, [콘솔로 이동](https://console.firebase.google.com)합니다.
2. Create new project 버튼 클릭, project name을 정하고 create project
3. overview창에서 Add Firebase to your web app 클릭하면 시작에 필요한 모델들과 초기화 코드(initialization code)가 나옵니다.

#### html, js에 초기화 코드 넣기
```
<script src="https://www.gstatic.com/firebasejs/3.6.6/firebase.js"></script>
```

```
// Initialize Firebase
var config = {
apiKey: "---",
authDomain: "---",---,
storageBucket: "---",
messagingSenderId: "---"
};
firebase.initializeApp(config);
```
이 작업만 하면 기본적인 파이어베이스 세팅이 됩니다.

> 여기서 잠깐!
Windows OS 에서 크롬에서는 overview창이 열리지 않습니다. 아마.. 큰 문제인거 같은데 파이어베이스에서 모르는건지..
유투브 댓글을 보니 몇명이 써놨더라고요. 저만 그런지 알고 처음에 당황했는데, 혹시 몰라서 모바일(사파리)과 파이어폭스에서 열어보니 잘됩니다.. ㅋㅋ


## Realtime Events 목차
[value events](#value-events)
[child events](#child-events)

#### value events
객체, 데이터 등을 동기화시키는 데 좋습니다.

```
(function() {

  // Initialize Firebase
  var config = {
    apiKey: "---",
    authDomain: ---",
    databaseURL: "---",
    storageBucket: "---",
    messagingSenderId: "---"
  };
  firebase.initializeApp(config);

  // get element
  const preObject = document.getElementById('object');

  // database 참조를 만들어서 data를 실시간으로 동기화해보자.
  // create references
  const dbRefObject = firebase.database().ref().child('object');

  dbRefObject.on('value', snap => preObject.innerText = JSON.stringify(snap.val(), null, 3)); // 여백 3
})();
```

##### ref() 함수
database의 root로 접근하게 해주고, 객체의 child키를 생성합니다. 이제 필요한 값을 저장할 수 있습니다.

##### on() 메서드
가장 강력한 메서드로서

첫 매개변수 : 이벤트 타입. 실시간 동기화를 어느 단계까지 할지를 정해줍니다.
**value** : database의 변경이 있을 때 매번 콜백함수를 호출합니다.

두번째 매개변수 : 콜백함수
**snap** : 콜백함수의 매개변수로서 '데이터 스냅샷'이라고 불립니다.
데이터 스냅샷은 key name, 자식요소 반복방식 등을 return합니다.
그 값을 얻고 싶으면 지금처럼 .val()함수를 호출합니다. 값이 객체라면 객체 전체를 동기화합니다.
만약에 객체의 한 value가 바뀌어도, 객체 전체를 update하는데, 이를 state 동기화라고 합니다.

#### child events
데이터 동기화를 미세하게 조절할 수 있습니다. 특히 list를 다룰 때 유용합니다.
어떤 요소가 add, remove, update 되었을 때 특정 child 이벤트에 동기화시키고 싶을 때 사용합니다.

Firebase Overview/Database에서 `object`객체 프로퍼티에 JSON 객체를 넣어봅니다.
```
object
  hobbies: { "coffee" : "coffee" }

// 이렇게 하면 key가 coffee이고 값이 coffee인 JSON객체가 부여됩니다.
// 이렇게 리스트를 추가합니다.
```

js파일에서
```
// child_added : 리스트에 자식이 추가될 때만 작동합니다.
// 처음에 모든 리스트가 동기화되며, 그 후엔 변한 부분만 동기화합니다.
dbRefList.on('child_added', snap => {

  const li = document.createElement('li');
  // 각 항목의 key name을 li의 id값으로 준다.
  li.id = snap.key;  
  li.innerText = snap.val();
  ulList.appendChild(li);

});

// child_changed : 자식이 바뀔때만 작동  
dbRefList.on('child_changed', snap => {

  const liChanged = document.getElementById(snap.key);
  liChanged.innerText = snap.val();

});

// child_changed : 자식이 삭제될 때만 작동  
dbRefList.on('child_removed', snap => {

  const liRemove = document.getElementById(snap.key);
  liRemove.remove();

});
```

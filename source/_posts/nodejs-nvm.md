---
title: NVM(Node Version Manager)으로 node.js 버전관리하기
date: 2016-12-20 22:27:35
categories: [Back-End, node.js]
tags: [node.js, NVM]
---

[Node Version Manager](https://github.com/creationix/nvm)

![Node Version Manager](/image/nvm.jpg)

> webpack이 자꾸 안되었던 이유가 node.js의 버전때문이었습니다. 하아 ㅜㅜ 지금이라도 알았으니 다행.. ^^
gulp + webpack 설정으로 사용하고 싶어, 스터디 팀끼리 서로 정보 공유하며 씨름하다 결국엔 성공했습니다. ^^ 씐나씐나 ~~~

**Windows** 환경에서 **NVM**을 설치하여 **node.js 버전을 바꾸며 사용**하는 방법입니다.
(언제나 그렇듯 Mac은 쉽죠잉 : [맥은 여기 참조](http://blog.jeonghwan.net/2016/08/10/nvm.html))

1) 기존에 사용하던 node를 삭제합니다.
 윈도우의 경우 제어판의 프로그램 제거에서 삭제하면 됩니다.

2) [nvm을 설치합니다.](https://github.com/coreybutler/nvm-windows/releases) nvm-setup.zip 다운받아 설치

3) 터미널에서 `$ nvm install v4.4.6` 처럼 사용할 버전의 노드를 설치합니다.

4) `$ nvm ls` 로 설치된 버전을 확인 할 수 있습니다.
 ```
 $ nvm ls

  * 6.9.2 (Currently using 64-bit executable)
    4.4.6
 ```
위처럼 저는 기존에 사용하던 gulp를 위해 v4.x와 현재 사용할 webpack + gulp를 위해 v6.x를 설치하였습니다.

5) 노드 버전을 바꾸어봅니다. `$ nvm use 4.4.6`
node버전 확인 :  `$ node -v` 만약 node가 설치 안된 것 처럼 나올 때는 터미널을 껐다 켜봅니다.

6) gulp를 전역에 설치합니다. `$ npm install --global gulp`
주의할 점은 gulp가 버전별로 설치가 되어야 한다는 점입니다.
즉, `$ nvm use 4.4.6` 에서도 설치, `$ nvm use 6.9.2`로 바꿔서도 설치해줍니다.

7) 이제 프로젝트에 해당하는 node 버전으로 바꾼 후에 기존처럼 사용하면 됩니다.

---
title: Sliding Puzzle Game - JavaScript, Electron
date: 2017-10-13 22:02:44
categories: [Portfolio, Free Project]
tags: [JavaScript, Electron]
---

> JavaScript로 숫자퍼즐 게임를 만들어보라는 2차 코딩 테스트!가 주어졌었습니다.
UI는 Google검색으로 가장 마음에 드는 것을 정해 비슷하게 CSS로 만들어보았습니다.
이 퍼즐 게임 또한 한정된 시간내에서 최선을 다해 만들었던 과제입니다.

[결과화면 보기](https://sharryhong.github.io/full-stack/test02-sliding-puzzle/index.html)
[해당 소스 보기](https://github.com/sharryhong/full-stack/tree/master/test02-sliding-puzzle)

![결과 이미지](/image/puzzle.jpg)


### 특징 및 기능
- easy, hard모드는 radio 버튼의 value로 정해지고, 현재 easy는 10번, value는 100번 섞이게 되어있습니다.
- 처음에 랜덤으로 숫자를 섞으면 결과가 나오지 않을 수도 있다고 하여, 실제로 섞을 수 있는 경우(빈칸의 상하좌우)만 섞이게 하였습니다.


### 주요 코드
#### UI를 만드는 부분
```
function displayNum() {
  var html = ''
  for (let i = 0; i < xCol; i++) {
    html += '<tr>'
    for (let j = 0; j < yRow; j++) {
      if (numArray[i][j] == '') {
        html += '<td id="blank" class="btn" data-x="'+ j + '" data-y="' + i + '">' + numArray[i][j] + '</td>'
      } else {
        html += '<td class="btn num" data-x="'+ j + '" data-y="' + i + '">' + numArray[i][j] + '</td>'
      }
    }
    html += '</tr>'
  }
  puzzleTable.html(html)
```
- 변수 xCol, yRow은 퍼즐의 가로, 세로 개수 입니다.
- 엘리먼트를 만들면서 data-x, data-y라는 속성을 만들어주어,
나중에 `id = "blank"`인 **빈칸의 상하좌우 움직일 수 있는 앨리먼트**인지 알아냅니다.

#### 사용기술 : HTML, CSS, JavaScript, jQuery, Electron
Electron은 웹 기술로 데스크톱 애플리케이션을 만들게 해주는 프레임워크입니다.
[사용 방법은 여기 참고해주세요.](https://electron.atom.io/docs/tutorial/quick-start/)

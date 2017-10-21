---
title: 타자연습 Game - JavaScript, Ajax, JSON
date: 2017-10-14 16:27:52
categories: [Portfolio, Free Project]
tags: [JavaScript, Electron]
---

> JavaScript, Ajax, JSON으로 타자연습 게임를 만들어보라는 3차 코딩 테스트!
비교적 수월한 작업이었고, 재미있는 요소들을 넣어가며 작업했습니다. ^^


[결과화면 보기](https://sharryhong.github.io/full-stack/test03-typing/index.html)
[해당 소스 보기](https://github.com/sharryhong/full-stack/tree/master/test03-typing)

![결과 이미지](/image/tt.jpg)

### 특징 및 기능
- 30초 동안 json내의 단어들을 랜덤으로 뿌려줍니다.
- 맞으면 +10점, 틀리면 -10점의 점수가 반영됩니다.
- sweetalert.js 사용, 맞을 때와 틀릴 때 귀여운 gif사용 ^^

### 주요 코드
#### json파일내의 데이터를 랜덤으로 뿌려주기
```
$.getJSON("words.json", function(data) {
  words = data.words
})

// 랜덤으로 단어 하나씩 뽑아 해당 엘리먼트에 뿌려주기
function randomWord() {
  randomIndex = Math.floor(Math.random() * words.length)
  currentWord = words[randomIndex]
  showWord.text(currentWord)
}
```
#### 입력 창 관련 코드
```
inputText.keypress(function(event) {
  if (event.keyCode === 13) { // enter키
    let answerWord = $(this).val() // 입력 값
    $(this).val('') // 입력 값 비우기
    if (answerWord == currentWord) { // 정답일 때
      words.splice(randomIndex, 1)   // 원본 배열에서 삭제
      randomWord()
      correctNo++
      scoreNo += 10
      score(correctNo, wrongNo, scoreNo)
      bottom.css({
        "background-image": "url('good.gif')",
        "background-size": "115px"
      });
    } else { // 오답일 때
      randomWord()
      wrongNo++
      scoreNo -=10
      score(correctNo, wrongNo, scoreNo)
      bottom.css({
        "background-image": "url('nono.gif')",
        "background-size": "115px"
      });
```

#### 사용기술 : HTML, CSS, JavaScript, jQuery, Ajax, JSON, Electron
Electron은 웹 기술로 데스크톱 애플리케이션을 만들게 해주는 프레임워크입니다.
[사용 방법은 여기 참고해주세요.](https://electron.atom.io/docs/tutorial/quick-start/)

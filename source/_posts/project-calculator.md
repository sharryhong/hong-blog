---
title: 계산기(calculator) - JavaScript, Electron
date: 2017-10-13 21:33:11
categories: [Portfolio, Free Project]
tags: [JavaScript, Electron]
---

> JavaScript로 계산기를 만들어보라는 1차 코딩 테스트!가 주어졌었습니다.
이에 UI는 아이폰 계산기 앱을 본 따 만들었습니다.
숫자, 연산자 순으로 클릭시 잘 되고 있습니다. ㅋㅋ
잘 풀리지 않을 땐 친구에게 설명만 해도 자연스레 해결책이 떠오르더군요.. :)


[결과화면 보기](https://sharryhong.github.io/full-stack/test01-calculator/index.html)
[해당 소스 보기](https://github.com/sharryhong/full-stack/tree/master/test01-calculator)

![결과 이미지](/image/cal.jpg)

### 특징 및 기능
- `=`을 누르기 전까지 상단에 계산과정이 나오도록 하였습니다.
- 연산자 우선순위는 반영되지 않습니다. 

### 주요 코드
```
calculator: function() {
  var inputText = this.innerHTML
  cal.op = inputText
  showBox.innerHTML += inputText
  checkBtn = true
  if (!checkPreNum) {
    cal.preNum = Number(numInput.value)
    checkPreNum = true
  } else {
    cal.nextNum = Number(numInput.value)
    clearNum()
    cal.resultFn(cal.preOp)
    cal.preNum = cal.result
    if (cal.op == '=') {
      checkPreNum = false
      showBox.innerHTML += cal.result +', '
    }
  }
  cal.preOp = cal.op
},
resultFn: function(op) {
  switch (op) {
  case '+':
  cal.result = cal.preNum + cal.nextNum
  break;
  case '-':
  cal.result = cal.preNum - cal.nextNum
  break;
  case '*':
  cal.result = cal.preNum * cal.nextNum
  break;
  case '/':
  cal.result = cal.preNum / cal.nextNum
  break;
  }
  numInput.value = cal.result
}
```

#### 사용기술 : HTML, CSS, JavaScript, Electron
Electron은 웹 기술로 데스크톱 애플리케이션을 만들게 해주는 프레임워크입니다.
[사용 방법은 여기 참고해주세요.](https://electron.atom.io/docs/tutorial/quick-start/)

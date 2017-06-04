---
title: SASS Nesting(중첩)
date: 2016-12-19 16:14:28
categories: [Front-End, CSS/SASS]
tags: [SASS, Nesting]
---

![sass](/image/sass.png)

[해당 코드가 있는 Github 바로가기01](https://github.com/sharryhong/TIL/tree/master/sass/01_First_Sass)
[해당 코드가 있는 Github 바로가기02](https://github.com/sharryhong/FDS/tree/master/day22-sass)

## Nesting(중첩)
중첩은 **반복을 제거**하고 스타일링에 **분명한 DOM관계**를 보여줌으로서 코드를 **효율적**으로 만듭니다.

확장자가 SCSS, SASS 일 때 문법이 다른데,
SCSS파일의 경우는 기존의 CSS의 문법과 동일합니다.
```
.parent {
  color: blue;
  .child {
    font-size: 12px;
  }
}
```

SASS파일의 경우 `{}`를 쓰지 않고 들여쓰기로 구분합니다. `;`도 쓰지 않습니다.
```
.parent
  color: blue
  .child
    font-size: 12px
```

위의 SCSS와 SASS의 CSS 컴파일 결과는 같습니다.
```
.parent {
  color: blue;
}

.parent .child {
    font-size: 12px;
}
```

#### 속성에 관련한 Nesting `:`
```
.parent {
  font : {
    family: Roboto, sans-serif;
    size: 12px;
    decoration: none;
  }
}
```

컴파일 결과
```
.parent {
  font-family: Roboto, sans-serif;
  font-size: 12px;
  font-decoration: none;
}
```

#### `&` : 부모 참조 선택자. 중첩된 구조에서 사용합니다.
```
.button
  &:hover
     background: skyblue
```

컴파일 결과
```
.button:hover {
  background: skyblue;
}
```

#### `@extend` : 선택자 상속. 그룹핑 개념으로 선언된 다른 규칙의 내용을 상속받습니다.
```
$btn-radius: 4px
$btn-align: center
$btn-gap: .6em
$btn-bg: #fe9977

.button
  display: inline-block
  padding: $btn-gap $btn-gap
  background: $btn-bg
  text-align: $btn-align

  &:hover
    background: skyblue

.button-error
  @extend .button
  color: #fff
  border: 3px solid green
```

컴파일 결과
```
.button, .button-error {
  display: inline-block;
  padding: 0.6em 0.6em;
  background: #fe9977;
  text-align: center; }
  .button:hover, .button-error:hover {
    background: skyblue; }

.button-error {
  color: #fff;
  border: 3px solid green; }
```

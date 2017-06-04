---
title: CSS 속성 선택자를 활용하여 각 파일포맷별 아이콘 설정하기
date: 2016-11-26 15:24:43
categories: [Portfolio, Free Project]
tags: [CSS, 선택자, 파일 포맷, 아이콘]
---

[해당 코드가 있는 Github 바로가기](https://github.com/sharryhong/TIL/blob/master/javaScript/02_class/js/tabmenu_v02.js) | [결과화면 보기](https://sharryhong.github.io/FDS/day06_css/02-css-file-format-type03.html)
<br>

![결과 이미지](/image/css-icons.jpg)

#### 속성 선택자
주로 특수한 상황인 요소를 찾을 때 쓰입니다.
`[class="snack"]` : classname이 반드시 snack인 요소 선택
`[class="snack seeu"]` : classname이 반드시 snack seeu인 요소 선택
`[class*="snack"]` : classname에 snack이 있는 요소 선택
`[class^="snack"]` : classname이 snack으로 시작하는 요소 선택  
`a[href$=".docx"]` : href 끝나는 값이 .docx인 a요소 선택
`a[href][title][data-href]` : 제시된 3가지 속성을 모두 가지고 있는 a요소 선택

#### 핵심 코드 설명

[html 파일](https://github.com/sharryhong/FDS/blob/master/day06_css/02-css-file-format-type03.html)

```
<li class="lecture-file-item">
	<a href="resources/file.aac">file-aac</a>
</li>
```
- 다운받을 파일명을 이용하여 background-image를 CSS에 미리 설정해 놓습니다.

[CSS 파일]((https://github.com/sharryhong/TIL/blob/master/javaScript/02_class/js/tabmenu_v02.js)
```
a[href$=".aac"] {
  background-image: url("../img/icon-aac.png");
}
...

a[href^="http://"][target="_blank"],
a[href^="https://"][target="_blank"] {
  background-image: url("../img/external-link.png");
}
```
- `^` 는 `처음 값`
- `$` 는 `마지막 값`
- `a[href$=".aac"]` : href속성 마지막 값이 .aac인 a요소 선택

### 연관 링크
[CSS 선택자에 관한 공부 링크 바로가기](https://github.com/sharryhong/FDS/tree/master/day06_css)

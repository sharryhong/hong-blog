---
title: SASS Satting
date: 2016-11-29 19:07:09
categories: [Front-End, CSS/SASS]
tags: [SASS, CSS]
---

{% asset_img thumb.png [sass] %}

[해당 코드가 있는 Github 바로가기](https://github.com/sharryhong/FDS/tree/master/day22-sass)

CSS Preprocessor 인 SASS. 웹 스타일링을 담당하는 CSS를 좀 더 똘똘하게 사용하고 유지보수를 좋게하는 프리프로세서입니다.

## 설치 및 Sass to CSS 
Sass to CSS를 위해 node sass를 실행합니다. 추후엔 Gulp같은 자동화툴로 관리하도록 합니다. 

### [다운로드 및 설치](https://git-scm.com)
git bash : 터미널 방식으로 명령어를 사용하여서 Git를 컨트롤 하는 시스템
설치 후 파일탐색기 > 해당폴더 > 마우스 오른쪽 > git bush here 를 클릭하여 터미널을 실행시킵니다. 

##### node sass 설치
```
$ npm install node-sass --global 혹은 
$ npm i -g node-sass (install global줄여쓴 것)
```

### sass -> css로

1. sass or scss파일을 만들고 저장 후 

 ```
 $ node-sass -w sass/ -o css/ --source-map css 
 ```
 sass폴더내의 sass or scss 파일을 css폴더내의 css파일로 컴파일한다는 뜻
 sourcemapping이 있어야 개발자도구에서 style.sass이런식으로 표시가 됩니다.

2. css 폴더내에 xxx.css.map 파일이 생깁니다. 배포시엔 map파일을 제외하고 올립니다. 

3. sass파일을 수정 후 저장합니다. 

4. 자, 이제 sass -> css파일로 컴파일 되었습니다. 이젠 css파일은 건드리지 않고 sass파일로만 작업합니다. 

### 파일 쪼개고 병합하기 

예를들어 `_footer.sass`와 같이 `_`가 붙으면 병합될 파일이므로 컴파일되지 않습니다. 
style.sass 에서 `@import /part/page/footer` 이런 식으로 @import 하여 병합시킵니다. 
@import시 파일이름의 `_`, `.sass`, `.scss`는 생략할 수 있습니다. 

### Sublime Text에서 sass, scss 파일 인지시키기 

1. Sublime Text의 install package에서 syntax highlighting for sass를 설치합니다. 
2. 서브라임 텍스트의 오른쪽 하단에서 sass를 선택합니다. 

##### 참고 사이트 
- [Sass-lang.com](http://sass-lang.com/) 
![Sass](thumb.png)  
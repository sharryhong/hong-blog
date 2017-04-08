---
title: SASS Variables (변수)
date: 2016-12-19 15:27:48
categories: [Front-End, CSS/SASS]
tags: [SASS, Variables]
---

{% asset_img thumb.png [sass] %}

[해당 코드가 있는 Github 바로가기01](https://github.com/sharryhong/TIL/tree/master/sass/01_First_Sass)
[해당 코드가 있는 Github 바로가기02](https://github.com/sharryhong/FDS/tree/master/day23-sass)

CSS로 style 코드를 작성하다보면 반복사용 하는 것들을 한번에 관리하면 좋겠다는 생각을 하게 됩니다. 
이럴 때 사용하면 좋을 문법이 sass의 **변수**입니다. 나중엔 mixin, 함수 개념등을 알면 좋은데 우선 변수만 잘 써도 일이 확 줄어드는 것을 알 수 있습니다. 조으다! ^^

## Variables (변수)
변수는 가독성과 유지보수를 향상시켜줍니다.

문법 : `$`를 붙여 변수를 만들고 값을 대입합니다. 
```
// 변수 선언 
$translucent-white: rgba(255,255,255,0.3);

// 변수 사용시 
background-color: $translucent-white;
```

#### 변수이름 작성 규칙
변수 이름 사이에 공백을 사용하지 않습니다.
변수 이름의 음절 사이에 `_` , `-` 등을 사용합니다. `_` , `-` 구별을 하지 않습니다.
만약 프로그래밍에 익숙해서 camelCase방식이 익숙하다면 사용이 가능하지만 camelCase방식은 함수 이름에 사용되므로 권장하지는 않습니다.

`!global` : 전역변수처럼 사용가능하게 합니다. 
```
#main {
  $width: 5em !global;
  width: $width;
}

#sidebar {
  width: $width;
}
```

`!default` : 기본값. null값을 제외하곤 다른 값이 우선시됩니다.
```
$set-width: 900px;
$set-width: 1000px !default
// 의 경우 900px로 됩니다. 
```

#### Data Type (데이터 유형)

| 데이터유형      |    설명 | 예  |
| :-------- | --------:| :--: |
| null  	| 빈 값 |   |
| number    | 숫자 |1.2, 3, 14px (특이하게 단위가 붙어도 숫자형입니다.)|
| string    |문자|color (#, rgba, ...) "../img/icon.jpg", 'Time, serif', #333|
| boolean    |논리. true, false| |
| list    |배열 개념|`1.5em Helvetica bold;` or `Helvetica, Arial, sans-serif;`|
| map    |객체 개념|`(key1: value1, key2: value2);`|
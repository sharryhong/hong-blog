---
title: JavaScript ES6 문법 - spread operator
date: 2017-02-27 00:26:16
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, spread operator]
---

{% asset_img js.png [JavaScript] %}

### spread operator(`...`)
copy목적으로 씁니다. 
length를 갖고 있는, 즉 순회를 할 수 있는 대상들(배열, 문자열)에 적용가능합니다. 


```
const defaultColors = ['red', 'green'];
const userFavoriteColors =['yellow', 'orange'];

// ES5
defaultColors.concat(userFavoriteColors); // ["red","green","yellow","orange"]

// ES6 
[ ...defaultColors, ...userFavoriteColors, 'blue' ]; // ["red","green","yellow","orange","blue"]
```

rest parameter와 함께 사용

```
function shoppingList(...items){
  if(items.indexOf('milk') < 0){ // milk가 없다면
    return ['milk', ...items]; // ["milk","bread","eggs"] 반환
  }
  return items;
}

shoppingList('bread', 'eggs');
```

### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)
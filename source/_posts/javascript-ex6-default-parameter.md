---
title: JavaScript ES6 문법 - default parameter
date: 2017-03-01 01:10:19
categories: [Front-End, JavaScript]
tags: [JavaScript, ES6, default parameter]
---

{% asset_img js.png [JavaScript] %}

### default parameter 

아래 함수처럼 파라미터 개수에 맞지 않게 함수를 실행시킨다면 오류를 발생시킵니다. 
```
const sum = function(x,y){
    return x+y;
}
sum(); // NaN 

```

ES6에서는 파라미터에 기본 값을 할당해줄 수 있습니다. 
```
const sum2 = function(x=5,y=10){
    return x+y;
}
sum2(); // 15
```


각 파라미터는 내부에서 let과 동일하게 동작하기 때문에 TDZ가 존재합니다. 
[TDZ에 관한 포스팅](https://sharryhong.github.io/2016/12/25/javascript-es6/)
```
function multiply(x = y * 3, y){
  console.log(x * y);
}
multiply(2, 3); // 6
multiply(undefined,2); // 레퍼런스 에러. TDZ. 

```

예 : 기본을 GET방식으로 지정해주고자 할 때 
```
function makeAjaxRequest(url, method = 'GET'){
  return method;
}

makeAjaxRequest('google.com');
makeAjaxRequest('google.com', 'POST');
```


예 : user에게 id를 부여하기. admin user에게는 id를 부여하는 것이 default로 적용되게 할 때 
```
// 생성자 함수
function User(id){
  this.id = id;
}

function generateId(){
  return Math.random() * 999999; // 유니크한 id생성
}

// Admin user생성을 위해서는 먼저 user로 생성되어야한다. 
// 이를 위해 default parameter 사용
function createAdminUser(user = new User(generateId())){
  user.admin = true;
  return user;
}

// 일반 user. 인스턴스 객체 생성, id부여 
const user = new User(generateId());

// admin user.  
createAdminUser(user);
```

### 참고 자료
[고무곰님 블로그](https://gomugom.github.io/es6-for-react/index.html)
[Udemy - ES6 Javascript: The Complete Developer's Guide](https://www.udemy.com/javascript-es6-tutorial)

### ES6 포스팅
[변수선언 let, const](https://sharryhong.github.io/2016/12/25/javascript-es6/)
[Blocks and IIFEs](https://sharryhong.github.io/2017/02/02/javascript-es6-blocks/)
[Strings 문자열표기법 등](https://sharryhong.github.io/2017/02/03/javascript-es6-string/)
[Arrow functions](https://sharryhong.github.io/2016/12/26/javascript-es6-arrow-functions/)
[Class](https://sharryhong.github.io/2017/02/06/javascript-es6-class/)
[rest parameter](https://sharryhong.github.io/2017/02/26/javascript-ex6-restparameter/)
[spread operator](https://sharryhong.github.io/2017/02/27/javascript-ex6-spread-operator/)
[default parameter](https://sharryhong.github.io/2017/03/01/javascript-ex6-default-parameter/)
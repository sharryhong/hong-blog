---
title: Algorism - 평균구하기 (JavaScript)
date: 2017-01-13 16:21:28
categories: [plus forWeb!, Algorism]
tags: [JavaScript, Algorism]
---

{% asset_img al.jpg [tryhelloworld] %}

## 알고리즘 02. 평균구하기 (JavaScript)

> def average(list):
함수를 완성해서 매개변수 list의 평균값을 return하도록 만들어 보세요.
어떠한 크기의 list가 와도 평균값을 구할 수 있어야 합니다.

#### 처음 나의 코딩
1) 목표 : 배열 값을 모두 더하여 length만큼 나눠 평균을 구하자. 

2) 매개변수로 들어온 배열.length의 경우 2번이상 쓰이므로 변수에 저장하자. 

```
function average(array){
  var result = 0;
  var arrLength = array.length;
  for(var i = 0; i < arrLength; i++){
    result += array[i];
  }
  return result/arrLength;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
var testArray = [5,3,4] 
console.log("평균값 : " + average(testArray));
```

#### 다른분의 코딩을 참고한 코드 리펙토링
ES6문법으로 코드 리펙토링해보았습니다. 
우선 let 선언으로 정의된 블록내에서만 존재하는 지역변수로 설정하고, 
for of문을 사용하여 각 배열 값이 자동으로 더해지게 하였습니다. 
주의사항 : for of문의 경우 브라우저 호환이 안되는 경우가 많습니다. 

```
function average(array){
  let result = 0;
  for(let item of array){
    result += item;
  }
  return result/array.length;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
var testArray = [5,3,4] 
console.log("평균값 : " + average(testArray));
```

[**for of문**](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/for...of)
for...of 문(statement)은 반복가능한 객체 (Array, Map, Set, String, TypedArray, arguments 객체 등을 포함)에 대해서 반복하고 각 개별 속성값에 대해 실행되는 문이 있는 사용자 정의 반복 후크를 호출하는 루프를 생성합니다. 
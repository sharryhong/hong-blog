---
title: JavaScript Array - find, every, some, reduce 내장 메소드
date: 2017-02-13 16:48:40
categories: [Front-End, JavaScript]
tags: [JavaScript, Array]
---

{% asset_img js.png [JavaScript] %}

## 반복자 함수 2. find, every, some, reduce (추후 추가)

#### 목차

[find 메소드](#find-메소드)

## [find 메소드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
콜백함수가 요구하는 조건을 만족하는 첫번째 값을 하나 반환합니다. 없으면 undefined를 반환합니다. 

```
arr.find(callback[, thisArg])
```

##### 예: 특정 프로퍼티, 값을 가지는 첫번재 객체를 찾는 함수를 완성해보세요. 
주어진 문제 : 
```
var ladders = [
  { id: 1, height: 20 },
  { id: 3, height: 25 }
];

function findWhere(array, criteria) {
  // array 중에서 criteria 에 해당하는 첫번째 객체를 찾아 반환하는 함수 만들기 
}

findWhere(ladders, { height: 25 }); 
```

result: `{ id:3, height: 25 }` 이어야 합니다. 

나의 문제 풀이 : 
```
function findWhere(array, criteria) {

  var key = Object.keys(criteria)[0]; 
  // criteria = { height: 25 }
  // Object.keys(criteria)[0] = height

  return array.find(function(arr){
  // ladders의 height값이 25인 것을 찾아 반환한다. 
    return arr[key] === criteria[key];
  });
}
```

[Object.keys(obj)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) : obj에 들어가는 객체의 프로퍼티 name들을 배열로 반환합니다. 

<sup>[(목차로 돌아가기)](#목차)</sup>
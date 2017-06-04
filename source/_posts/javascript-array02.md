---
title: JavaScript Array - forEach, map, filter 내장 메소드
date: 2017-02-13 13:54:50
categories: [Front-End, JavaScript]
tags: [JavaScript, Array]
---

![JavaScript](/image/js.png)

## 반복자 함수 1. forEach, map, filter

#### 목차

[forEach 메소드](#forEach-메소드)
[map 메소드](#map-메소드)
[filter 메소드](#filter-메소드)

## [forEach 메소드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
배열의 각 요소에 대해 한번씩 순서대로 콜백함수를 실행합니다.

```
arr.forEach(callback[, thisArg])
```

**callback 함수** : 배열의 각 요소에 대해 실행할 함수로 다음 세 가지 인수를 가집니다.
1) currentValue : 배열의 요소 중, 현재 처리되고 있는 요소
2) index : 현재 처리되는 요소의 배열 내 인덱스
3) array : forEach 메소드가 적용되는 본래 배열

thisArg : 선택항목. callback을 실행할 때 this로 사용되는 값.

##### 예) forEach를 사용하여 images 각 요소의 areas(넓이) = height * width 를 계산하여 areas 배열에 넣어보세요.
```
var images = [
  { height: 10, width: 30 },
  { height: 20, width: 90 },
  { height: 54, width: 32 }
];
var areas = [];
```

forEach 메소드를 사용함으로서 좀 더 명시적으로 코드구현을 할 수 있습니다.
```
function imgErea(img) {
	areas.push(img.height * img.width);
}

images.forEach(imgErea);
```

<sup>[(목차로 돌아가기)](#목차)</sup>

## [map 메소드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
배열의 각각의 요소에 대해 한번씩 순서대로 콜백함수를 실행하고, 그 결과를 모아서 새로운 배열을 반환합니다.

```
arr.map(callback[, thisArg])
```

**callback 함수** : 새로운 배열 요소를 생성하는 함수로 다음 세 가지 인수를 가집니다.
1) currentValue : 배열의 요소 중, 현재 처리되고 있는 요소
2) index : 현재 처리되는 요소의 배열 내 인덱스
3) array : map 메소드가 적용되는 본래 배열

thisArg : 선택항목. callback을 실행할 때 this로 사용되는 값. 기본값은 Window 객체.

```
var ages = [10, 21, 17, 34, 19];
var adult = ages.map(function(age){
    return age >= 18;
});

console.log(adult);

// 결과
[false, true, false, true, true]
```

##### 예) map을 사용하여 css속성과 값이 객체로 담겨져 있는 배열에서, 해당 css 속성 값만 저장하는 배열을 만들어보세요.
매개변수 1 : css 속성과 값이 객체로 담겨져 있는 배열, 매개변수 2 : css 속성

```
var paints = [ { color: 'red' }, { color: 'blue' }, { color: 'yellow' }];


function pluck(array, property) {

  var proValue = array.map( (obj) => {
    return obj[property];
  });

  return proValue;
}

pluck(paints, 'color'); // returns ['red', 'yellow', 'blue'];
```

<sup>[(목차로 돌아가기)](#목차)</sup>


## [filter 메소드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
배열 내 각 요소에 대해 제공된 콜백함수에서 true를 반환하는 모든 값이 있는 새로운 배열을 반환합니다.
즉, 콜백 테스트를 통과한 배열 요소만 반환되고, 통과하지 못한 배열 요소는 건너뛰어 새로운 배열에 포함되지 않습니다.

```
var new_array = arr.filter(callback[, thisArg])
```

**callback 함수** : 배열의 각 요소에 대해 실행할 함수로 다음 세 가지 인수를 가집니다.
1) currentValue : 배열의 요소 중, 현재 처리되고 있는 요소
2) index : 현재 처리되는 요소의 배열 내 인덱스
3) array : filter 메소드가 적용되는 본래 배열

thisArg : 선택항목. callback을 실행할 때 this로 사용되는 값.
return값 : 테스트를 통과한 요소가 있는 새로운 배열

##### 예) 댓글의 postId와 포스팅 id가 같은 것 걸러내기  
```
var post = { id: 5, title: 'for front-end'  };
var comments = [
  { postId: 4, content: 'JavaScript first and web framework' },
  { postId: 5, content: 'HTML, CSS' },
  { postId: 5, content: 'server' }
];

function commentsPost(post, comments) {
  return comments.filter(function(comment) {
    return comment.postId === post.id;
  });
}

commentsPost(post, comments);
// [{"postId":5,"content":"HTML, CSS"},{"postId":5,"content":"server"}]
```


<sup>[(목차로 돌아가기)](#목차)</sup>


### 연관 포스팅
[JavaScript Array 내장 프로퍼티, 메소드](https://sharryhong.github.io/2017/01/07/javascript-array/)

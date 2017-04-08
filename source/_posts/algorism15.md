---
title: Algorism - 수열의 곱과 합.. 최소값 만들기 (JavaScript)
date: 2017-01-30 13:31:58
categories: [plus forWeb!, Algorism]
tags: [JavaScript, Algorism]
---

{% asset_img al.jpg [tryhelloworld] %}

## 알고리즘 15. 최소값 만들기 (JavaScript)

> 자연수로 이루어진 길이가 같은 수열 A,B가 있습니다. 최솟값 만들기는 A, B에서 각각 한 개의 숫자를 뽑아 두 수를 곱한 값을 누적하여 더합니다. 이러한 과정을 수열의 길이만큼 반복하여 최종적으로 누적된 값이 최소가 되도록 만드는 것이 목표입니다.
예를 들어 A = [1, 2] , B = [3, 4] 라면
1) A에서 1, B에서 4를 뽑아 곱하여 더합니다.
2) A에서 2, B에서 3을 뽑아 곱하여 더합니다.
수열의 길이만큼 반복하여 최솟값 10을 얻을 수 있으며, 이 10이 최솟값이 됩니다.
수열 A,B가 주어질 때, 최솟값을 반환해주는 getMinSum 함수를 완성하세요.

#### 나의 코딩
1) 우선 배열 값끼리 곱하여 더하기를 반복문을 돌려 구한 뒤 최소값을 구하려고 해보았더니, 배열 index 갯수가 많아지면 복잡해져 다른 방법을 생각해보기로 했습니다. 

2) 하나의 배열은 작은 숫자대로 정렬하고, 하나의 배열은 큰 숫자대로 정렬하여 같은 index 값끼리 곱하여 전체를 더해주면 최소값이 나온다는 것을 생각하였습니다. 

3) JavaScript의 [Array.prototype.sort() 내장 메서드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)를 사용하여 정렬합니다. 

4) 그런데 sort()는 문자열에 따르므로 숫자의 경우 크기대로 정렬이 되지 않습니다. 
예를 들어 23, 1004의 경우 1004가 앞에 오게 됩니다. 
레퍼런스를 읽어보니 배열 index 값 앞뒤 비교를 하여 
```
function compare(a, b) {
  if (a is less than b by some ordering criterion) {
    return -1;
  }
  if (a is greater than b by the ordering criterion) {
    return 1;
  }
  // a must be equal to b
  return 0;
}
```
a(앞 값), b(뒤 값) 비교를 하여 0보다 작으면 a가 작은 값, 
0보다 크면 b가 작은 값입니다. 이를 간단하게 아래처럼 코딩할 수 있습니다.
```
function compareNumbers(a, b) {
  return a - b;
}
```

5) 이렇게 sort()에 대하여 알아보고 코딩해봅니다. 

```
function getMinSum(A,B){
  var answer = 0;
  A = A.sort(compareNum);
  B = B.sort(compareNum).reverse();
  var leng = A.length;
  for( var i = 0; i < leng; i++ ) {
    answer += A[i] * B[i];
  }
  return answer;
}

function compareNum(a, b) {
  return a - b;
}

getMinSum([189,2309,457,4594,7315,7551,7782,8311,8582,9664],[9624,8663,6130,5866,547,357,3392,3206,3070,302]);
```

> 처음엔 sort()가 문자열대로 정렬되어 값이 틀리게 나왔었습니다. 그 후 레퍼런스를 자세히 본 뒤 수정하였습니다. 
다른분들 풀이를 보니 reverse() 내장메서드를 쓰지 않고 아래처럼 구현하였습니다. 
```
A.sort(function(a,b){return a-b;});
B.sort(function(a,b){return b-a;});
```
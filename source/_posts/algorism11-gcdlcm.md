---
title:  Algorism - 최대공약수와 최소공배수 (JavaScript)
date: 2017-01-17 15:52:00
categories: [plus forWeb!, Algorism]
tags: [JavaScript, Algorism]
---

{% asset_img al.jpg [tryhelloworld] %}

> 최대공약수, 최소공배수.. 오랜만에 다시 보았네요 ㅋㅋㅋ 

## 알고리즘 11. 최대공약수와 최소공배수 (JavaScript)

> 두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환해주는 gcdlcm 함수를 완성해 보세요. 배열의 맨 앞에 최대공약수, 그 다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 gcdlcm(3,12) 가 입력되면, [3, 12]를 반환해주면 됩니다.

#### 처음 나의 코딩 
1) 우선 둘 중 작은 수를 minNum, 큰 수를 maxNum로 다시 세팅한다. 

2) 최소공배수 : 두 수의 공통된 배수(공배수) 중 가장 작은 수
 minNum * maxNum / 최대공약수 

3) 최대공약수 : 두 수의 공통된 약수(공약수) 중 가장 큰 수
 두 수를 나눠봐서 나머지가 0이면 (즉 나눠지면) maxNum가 최대 공약수이고, 
 나머지가 생긴다면 maxNum와 나머지값을 다시 비교합니다. 

```
function gcdlcm(a, b) {
    var answer = [];
    var minNum = Math.min(a, b);
    var maxNum = Math.max(a, b);
    answer[0] = gcd(minNum, maxNum);
    answer[1] = lcm(minNum, maxNum);
    return answer;
}
// 최대공약수 
function gcd(minNum, maxNum){
  return (minNum % maxNum) === 0 ? maxNum : gcd(maxNum, minNum % maxNum);
}
// 최소공배수 
function lcm(minNum, maxNum){
  return minNum * maxNum / gcd(minNum, maxNum);
}
// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(gcdlcm(3,12));
```
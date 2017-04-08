---
title: Algorism - 피보나치 수열 (JavaScript)
date: 2017-01-24 15:16:24
categories: [plus forWeb!, Algorism]
tags: [JavaScript, Algorism]
---

{% asset_img al.jpg [tryhelloworld] %}

## 알고리즘 13. 피보나치 수열 (JavaScript)

> 피보나치 수는 F(0) = 0, F(1) = 1일 때, 2 이상의 n에 대하여 F(n) = F(n-1) + F(n-2) 가 적용되는 점화식입니다. 
2 이상의 n이 입력되었을 때, fibonacci 함수를 제작하여 n번째 피보나치 수를 반환해 주세요. 
예를 들어 n = 3이라면 2를 반환해주면 됩니다. 

[피보나치 수 - 위키피디아](https://ko.wikipedia.org/wiki/%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98_%EC%88%98)

#### 나의 코딩 
1) 피보나치가 잘 고안해 낸 식을 그대로 써서, 매개변수가 0, 1일 땐 매개변수 자체를 반환하고, 1보다 클 때는 매개변수가 0, 1이 될때까지 함수를 실행하게끔 `F(n) = F(n-1) + F(n-2)` 대로 해보자. 

```
function fibonacci(num) {
	var answer = 0;

	if( num <= 1 ) {
		return num;
	} 
	else if( num > 1 ) {
		answer = fibonacci(num-1) + fibonacci(num-2);
	}
	return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(fibonacci(3));
```

> 생각과 그대로 잘 실행이 되었다. 피보나치 레오나르도 수학자님 짱 ㅋㅋㅋ 
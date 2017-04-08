---
title: Algorism - 약수의 합 (JavaScript)
date: 2017-01-25 16:42:03
categories: [plus forWeb!, Algorism]
tags: [JavaScript, Algorism]
---

{% asset_img al.jpg [tryhelloworld] %}

## 알고리즘 14. 약수의 합 (JavaScript)

> 어떤 수를 입력받아 그 수의 약수를 모두 더한 수 sumDivisor 함수를 완성해 보세요. 예를 들어 12가 입력된다면 12의 약수는 [1, 2, 3, 4, 6, 12]가 되고, 총 합은 28이 되므로 28을 반환해 주면 됩니다.

약수(divisor)는 어떤 정수를 나누어 떨어지게 하는, 0이 아닌 정수를 말하며,
음의 정수도 약수가 되지만 일반적으로 양의 약수만 다룹니다.

#### 나의 코딩
1) 약수는 나눠 떨어지는 정수를 구하면 됩니다. 
for문으로 1부터 해당 값까지, % 나머지 값이 0인 값을 구하면 될 것 같습니다. 

```
function sumDivisor(num) {
	var answer = 0;

	for(var i = 1; i <= num; i++) {
		if(num % i === 0) {
			answer += i;
		}
	}
	return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(sumDivisor(12));
```

> 생각과 그대로 잘 실행이 되었습니다. ^^ 
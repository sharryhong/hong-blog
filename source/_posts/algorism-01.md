---
title: Algorism - 핸드폰번호 가리기 (JavaScript)
date: 2017-01-13 01:35:55
categories: [plus forWeb!, Algorism]
tags: [JavaScript, Algorism]
---

![tryhelloworld](/image/al.jpg)

> 한국에도 이런 사이트가 있어 기쁩니다. ^^
해외에는 codecademy, udacity, udemy.. 등의 우수한 강의사이트가 있는데 tryhelloworld도 못지않게 훌륭하네요!
JavaScript에 해당하는 알고리즘을 풀고난 후, 다른사람들의 풀이를 보니 공부에 많은 도움이 되고 있습니다. :)  

## 알고리즘 01. 핸드폰번호 가리기 (JavaScript)

> 별이는 헬로월드텔레콤에서 고지서를 보내는 일을 하고 있습니다. 개인정보 보호를 위해 고객들의 전화번호는 맨 뒷자리 4자리를 제외한 나머지를 "\*"으로 바꿔야 합니다.
전화번호를 문자열 s로 입력받는 hide_numbers함수를 완성해 별이를 도와주세요
예를들어 s가 "01033334444"면 "\*\*\*\*\*\*\*4444"를 리턴하고, "027778888"인 경우는 "\*\*\*\*\*8888"을 리턴하면 됩니다.

#### 처음 나의 코딩
1) 목표 : 문자열 중 마지막 4개만 제외하고 별표로 바꿔야한다.
 : 문자열 length만큼 for문을 돌면서 별표로 바꾸자. (length - 4까지)

2) 내가 아는 내장 메소드 중 문자열을 배열값으로 분리하여 저장하는 split()로 하나하나 값을 지정할 수 있게 한다.

3) for문을 돌며 각 배열 값을 별표로 바꾸자.

4) join() 메소드로 배열의 모든 요소를 연결하여 문자열로 만들어보자.

```
function hide_numbers(s){
	var result = "";
	result = s.split("");
	for(var i = 0; i < result.length - 4; i++){
		result[i] = "*";
	}
	return result.join("");
}

console.log("결과 : " + hide_numbers('01033334444'));
```

#### 다른분의 코딩을 참고한 코드 리펙토링
배열로 바꾸지 않고 바로 별표를 대입시킨 코드
if문을 삼항식으로 적용하여 한줄로 간단하게 적용한 코드

```
function hide_numbers(s){
	var result = "";
	var sLength = s.length;
	for(var i = 0; i < sLength; i++){
		result += i < sLength - 4 ? "*" : s.charAt(i);
	}
	return result;
}

console.log("결과 : " + hide_numbers('01033334444'));
```

charAt()이라는 메소드를 공부해보았습니다.
`str.charAt(index)` 문자열에서 index 문자를 반환합니다.
if문을 삼항식으로 써보았습니다. 문자열의 길이 s.length - 4 보다 작다면, 즉, 마지막 4개 이전의 index 값에는 *를 대입하고, 나머지는 원래의 s.charAt(i)값을 대입합니다.

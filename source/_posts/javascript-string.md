---
title: JavaScript String 프로퍼티, 메소드
date: 2017-01-09 13:58:17
categories: [Front-End, JavaScript]
tags: [JavaScript, String]
---

{% asset_img js.png [JavaScript] %}

> Free Project를 진행하면서 자주 사용하는 프로퍼티, 메소드 등을 계속 추가할 예정입니다. :)

#### 목차
[charAt 메소드](#charAt-메소드)
[replace 메소드](#replace-메소드)
[repeat 메소드](#repeat-메소드)
[slice 메소드](#slice-메소드)
[substring 메소드](#substring-메소드)

## [charAt 메소드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)
문자열에서 특정 위치의 문자를 구할 수 있습니다. 

```
str.charAt(index)
```
index : 문자열의 위치 인덱스 값으로 0부터 시작 
리턴값 : index 위치의 문자 

알고리즘 코드에 올린 내용입니다. 
마지막 번호 4개를 제외하고 *로 보이게 하기 (핸드폰번호 가리기)
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

문자열의 길이 s.length - 4 보다 작다면, 즉, 마지막 4개 이전의 index 값에는 *를 대입하고, 나머지는 원래의 s.charAt(i)값을 대입합니다. 

<sup>[(목차로 돌아가기)](#목차)</sup>

## [replace 메소드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
어떤 패턴에 일치하는 일부 또는 모든 부분이 교체된 새로운 문자열을 반환합니다.

String.prototype.replace()

#### 문법
```
str.replace(regexp|substr, newSubStr|function)
```
regexp : 정규표현식, substr : 문자열
newSubStr : 새로운 문자열, function : 함수

#### 예) 속성 class 값 중 'no-js' 값을 'js'로 변경하기
```
var html_class_attr = element.getAttribute('class');
element.setAttribute('class', html_class_attr.replace(/no-js/,'js'));
```

<sup>[(목차로 돌아가기)](#목차)</sup>

## [repeat 메소드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)

```
str.repeat(count)
```
**count** : 0이상의 정수. 기존의 문자열을 반복할 횟수 
리턴값 : 횟수만큼 복사를 포함하는 새 문자열 

```
"abc".repeat(2); // 결과 : // "abcabc"
```

###### 브라우저 호환 : IE, 오페라 지원안함 
ES6에서 추가된 메소드입니다. 

<sup>[(목차로 돌아가기)](#목차)</sup>

## [slice 메소드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
지정한 문자열 시작위치 ~ 끝위치까지의 문자열을 반환합니다.

```
str.slice(beginSlice[, endSlice])
```

<sup>[(목차로 돌아가기)](#목차)</sup>

## [substring 메소드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substring)

```
str.substring(indexStart[, indexEnd])
```
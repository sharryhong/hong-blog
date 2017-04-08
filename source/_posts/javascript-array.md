---
title: JavaScript Array 프로퍼티, 메소드
date: 2017-01-07 14:22:51
categories: [Front-End, JavaScript]
tags: [JavaScript, Array]
---

{% asset_img js.png [JavaScript] %}

> Free Project를 진행하면서 자주 사용하는 프로퍼티, 메소드 등을 계속 추가할 예정입니다. :)

#### 목차
[length 프로퍼티](#length-프로퍼티)
[indexOf 메소드](#indexOf-메소드)
[splice 메소드](#splice-메소드)

## [length 프로퍼티](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/length)
배열의 원소 개수를 나타냅니다.

만약에 배열 index에 임의대로 값을 저장하면 length는 가장 큰 index를 기준으로 정해집니다. 
```
var arr = []; // 변수 배열로 초기화
console.log(arr.length); // 0

arr = [2,1,2]; // arr.length = 3
arr[100] = 5; 
console.log(arr.length); // 101 
```

##### 예) DOM 요소 개수만큼 class name 추가하기 

[해당 Free Project 바로가기](https://sharryhong.github.io/2017/01/04/project-gallery/)

```
// class="photo-link"인 요소들을 모두 선택합니다.
// 이 때 변수 photoLink에 요소들이 유사배열로 저장됩니다. 
var photoLink = document.querySelectorAll('.photo-link');

for(var i=0; i<photoLink.length; i++){

	photoLink[i].onclick = function() {
		// 클릭한 요소가 몇번째 index에 있는가 
		var idx = photoLink.indexOf(this);
		
		for(var j=0; j<photoLink.length; j++){
			// 클릭한 요소가 아닌 모든 요소 선택 
			if( j !== idx ) {
				photoLink[j].classList.toggle("off");
			}
		}
		// 클릭한 요소에 class name 토글(add, remove)
		this.classList.toggle("on");
	}
}

```

<sup>[(목차로 돌아가기)](#목차)</sup>


## [indexOf 메소드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
배열에서 지정된 요소를 찾을 수있는 첫 번째 인덱스를 반환하고 존재하지 않으면 -1을 반환합니다.

##### 예) 배열 중 지정한 값 삭제하는 함수 만들기
```
var originArray = [0,1,2,3,4,5];

function removeValue(originArray, idx) {
    // 매개변수 idx값이 몇번째 index인지 알아냅니다. 
    var idx_check = originArray.indexOf(idx);
    // 만약 -1이라면 배열에 없는 값이므로 false반환하고 끝냅니다. 
    if ( idx_check === -1 ) {
        return false;
    } 
    // 만약 -1보다 크다면 배열에 있는 값입니다. 
    if ( idx_check > -1 ) {
        // splice메소드를 사용하여 해당 index로부터 1개를 삭제합니다. 
        return originArray.splice(idx_check, 1);
    }
}

removeValue(originArray, 3); // 결과 originArray = [0,1,2,4,5]
```

<sup>[(목차로 돌아가기)](#목차)</sup>

## [splice 메소드](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
배열의 내용을 추가/제거하는 데 사용됩니다.

```
array.splice(start, deleteCount[, item1[, item2[, ...]]])
```
**start** : 변경이 시작되는 인덱스
**deleteCount** : 배열에서 제거를 할 요소의 수
**itemN** : 배열에 추가될 요소

<sup>[(목차로 돌아가기)](#목차)</sup>


### 참고 자료 
[Array - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
인사이드 자바스크립트 - 한빛미디어

### 연관 포스팅 
[JavaScript Array - forEach, map, filter 내장 메소드](https://sharryhong.github.io/2017/02/13/javascript-array02/)
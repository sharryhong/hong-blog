---
title: 스터디그룹모임 - Event(이벤트)
date: 2017-02-04 00:59:54
categories: [Front-End, JavaScript]
tags: [JavaScript, 이벤트 버블링]
---

![스터디그룹 홧팅!! ^^](/image/study_group.jpg)

> 설연휴로 인해 2주만에 만난 스터디모임 ^^ 알차고 재밋었던 시간이었습니다~
이번엔 **이벤트 버블링**, **이벤트 객체**, **이벤트 위임**, ES6, 알고리즘 등을 나눴는데,
그 중 이벤트에 대해 포스팅해보려합니다.

### 이벤트 버블링 (Event Bubbling)
이벤트 버블링이란 자식노드에서 부모노드 순으로 이벤트가 전파되는 것으로, 반대방향으로 전파되는 것은 캡쳐링이라고 합니다.
일반적으로 이벤트는 버블링됩니다.

![Event Capturing & Bubbling](01.png)

이벤트 버블링을 막으려면 stopPropagation() 메소드를 사용해야합니다.
```
document.querySelector(".cbtn").addEventListener("click", doSth);
function doSth(e) {
	e.stopPropagation();

	// do something
}
```

### 이벤트 객체
```
eventTarget.addEventListener("click", function(e){});
```

위의 코드에서 콜백함수의 매개변수로 들어간 e는 이벤트 객체를 말합니다.

##### 이벤트 객체의 주요 프로퍼티와 메소드
**event.target** : 현재 이벤트가 발생한 요소
**event.currentTarget** : 현재 이벤트가 발생한 DOM요소로 일반적으로 this와 같습니다.
**event.preventDefault()** : 현재 이벤트의 기본 동작을 중단합니다.
**event.stopPropagation();** : 현재 이벤트가 상위로 전파되지 않도록 중단합니다.

### 이벤트 위임 (Event Delegation)
위에서 살펴봤듯이 이벤트는 기본적으로 버블링되어 전파됩니다.
이런 성질을 이용해서 자식 요소가 자주 바뀌거나 너무 많을 경우, 공통된 부모 요소에 이벤트를 걸어두고 처리하는 방법을 말합니다.

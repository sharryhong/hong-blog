---
title: JavaScript DOM
date: 2016-12-28 22:18:11
categories: [Front-End, JavaScript]
tags: [JavaScript, DOM]
---

{% asset_img dom.png [JavaScript DOM] %}

> JavaScript를 배운다는 건...  
core(문법), core library(기본 제공 함수 등), BOM, DOM 
이 중 DOM에 대해 정리해보겠습니다. 

## DOM(Document Object Model)
노드, 스타일, 속성, 이벤트, 위치 및 크기 등을 다룰 수 있는 다양한 기능이 포함되어 있습니다. 
※ 노드 : HTML 웹페이지 구성요소의 가장 작은 단위로써 요소, 주석, 텍스트 등이 모두 노드에 해당합니다. 

### DOM과 HTML페이지의 관계
1. HTML페이지 로딩 
-> 2. 파싱(Parsing)을 거쳐 작성된 마크업 요소와 1:1로 매칭되는 DOM객체 생성(DOM Tree) 
예를들어, 파싱단계에서 `<div>`를 만나면 `HTMLDivElement`라는 클래스의 인스턴스(객체)를 생성하게 됩니다.
-> 3. 브라우저 화면에 출력 


### 핵심 DOM 객체 

**Node** : 노드를 다루는 기본 기능과 프로퍼티 제공. 노드를 탐색, 조작
※ 노드에는 Element node(요소), Text node(텍스트, 빈칸포함), 주석 노드 등도 모두 포함
**Document** : text node, element node, attribute node 생성
**Element** : 요소의 기본 기능과 프로퍼티 제공. 속성과 이벤트 제어 
**Text** : 텍스트를 다루는 기능
**Attribute** : 속성을 다루는 기능
**HTMLDocument** : Document객체를 확장하여 HTML용 프로퍼티와 메서드를 추가한 객체
**HTMLElement** : HTML요소의 기본 기능과 프로퍼티 제공. id, className, style등이 존재


| DOM객체 | Node | 
| :----- | :----- |
|상속구조|Node|
| 기능 | 노드 탐색, 조작하는 프로퍼티와 메서드|  
|주요 프로퍼티| `node.parentNode` 부모노드 탐색<br>`node.childNodes` 자식노드들 탐색<br>`node.firstChild` 첫번째 자식노드 탐색<br>`node.lastChild` 마지막 자식노드 탐색<br>`node.previousSibling` 이전 형제노드 탐색<br>`node.nextSibling`다음 형제노드 탐색<br>`node.children` 그 안의 요소만 가져옴. <br>빈칸은 textnode인데 가져오지 않으므로 편리하다. <br>`node.nodeName`요소의 이름을 대문자로 반환<br>`node.nodeType` 요소노드는 1, 텍스트노드 3, 주석노드 8<br>`node.nodeValue` 텍스트노드에만 접근 가능.<br> 텍스트 노드의 실제 값 반환. 요소노드의 경우는 null 반환<br>`node.hasChildNodes()` 자식이 있으면 true, 없으면 false<br><br>**※ 아래는 IE8이하는 안되나 요소만 찾아줌** <br> `node.parentElement` 부모요소 탐색 <br>`node.firstElementChild` 첫 자식요소 노드 탐색<br> `node.lastElementChild` 마지막 자식 요소 노드 탐색<br> `node.previousElementSibling` 이전 형제요소 탐색<br> `node.nextElementSibling` 다음 형제요소 탐색 |
|주요 메서드|`node.hasChildNodes()` true/false 반환<br>`node.hasChildNodes()` true/false 반환<br>`node.cloneNode(boolean)` false가 기본값. true면 자식까지 복제<br>`부모노드.appendChild(자식노드)` 부모의 꽁지쪽에 붙이기<br>`목표노드.부모노드.insertBefore(insert삽입할노드, target목표노드)` <br>`node.removeChild(childnode)`<br>`target_node.parentNode.replaceChild(replace_node, target_node)` <br>노드 교체. 위치를 교체하는 것이 아니라, 이전 노드를 삭제 한다.<br>이전 노드를 삭제하지만 결과 값으로 반환된다.|
|사용 예|`var el = document.getElementById('div-01').nextSibling;`

| DOM객체 | Document |
| :----- | ----- |
|상속구조|Node > Document||
| 기능 | Text node, Element node 생성 | 
|주요 프로퍼티| |
|주요 메서드| `document.createElement('element')` 요소 만들기. 실제 DOM에 붙는건 아님<br> `document.createTextNode('text')` 텍스트 노드 만들기 <br> `document.createAttribute("name");` 잘쓰지않음<br>`document.getElementById("idname");` id로 대상(요소노드)을 선택 <br>`document.getElementsByTagName("p");` 요소명으로 선택<br>`document.getElementsByClassName('classname');` 클래스명으로 선택<br>`document.querySelector(css selector);`막강!!! IE8이상. 첫번째 하나만 반환<br>`document.querySelectorAll(css selector);` 상동. 전체 복수로 반환<br>createEvent()<br>`target.addEventListener(type, listener[, options]);`<br>dispatchEvent()<br>removeListener()|


| DOM객체 | HTMLDocument | 
| :----- | ----- | 
|상속구조|Node > Document > HTMLDocument|
|기능|HTML문서 전용 프로퍼티, 메서드|
|주요 프로퍼티| |
|주요 메서드|close()<br>open()<br>write()<br>Element[]<br>getElementByName()|


| DOM객체 | Element |
| :----- | ----- | 
|상속구조|Node > Element|
|기능|속성을 다루는 기능, 이벤트 |
|주요 프로퍼티|`tagName` 요소의 이름반환. 예전방식|
|주요 메서드| Element[]<br>ElementsByTagName()<br>`element.hasAttribute(attName);` true/false 반환<br>`element.getAttribute(attributeName);`<br>`element.removeAttribute(attrName);`<br>`element.setAttribute(name, value);`<br>`target.addEventListener(type, listener[, options]);`<br>dispatchEvent()<br>removeListener()|
|사용 예|`var parent_el = document.getElementById('parent');` <br>`console.log('data-con:', parent_el.getAttribute('data-con'));`|


| DOM객체 | HTMLElement |
| :----- | ----- |
|상속구조|Node > Element > HTMLElement|
|기능| HTML요소 전용 프로퍼티, 메서드|
|주요 프로퍼티| `element.id`<br>`element.className`<br>`element.innerHTML = content;`노드 동적생성을 쉽게해줌<br>`element.style.color = "blue";`<br>`element.offsetWidth` border까지의 width<br>`element.offsetHeight` border까지의 height<br>`element.offsetLeft`<br>`element.offsetTop`|
|주요 메서드|onkeydown<br>onkeypress<br>onkeyup<br>onclick<br>ondbclick<br>onmousedown<br>onmousemove<br>onmouseout<br>onmouseover<br>onmouseup|
|사용 예| `var parent_el = document.getElementById('parent');`<br>`console.log('id:', parent_el.id);`<br>`console.log('class:', parent_el.className);`<br>`console.log('title:', parent_el.title);`|


### 참고 자료
[DOM - MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document)
[My Github 링크](https://github.com/sharryhong/FDS/tree/master/day29-javascript)
웹 프론트엔드 개발자를 위한, 자바스크립트+jQuery 완전정복 스터디 - 김춘경(딴동네) 

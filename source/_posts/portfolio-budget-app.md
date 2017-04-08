---
title: 예산관리 웹애플리케이션 - 01. 설계하기
date: 2017-01-22 22:11:58
categories: [Portfolio, Free Project]
tags: [JavaScript, 모듈패턴, 설계]
---

> 이번 프로젝트는 udemy 동영상 강의를 보면서 모듈패턴으로 개발해보려고 합니다.
영어로 된 강의인데도 강사가 아주 뛰어난지.. 왜 알아듣기 쉬운것이죠.. 자랑이 아니고 진짜임 :)
목표는 Structure, Architecture 즉, 데이터 구조 등의 설계부터 제대로 Front-End 개발을 하는 것으로, Firebase로 서버단 구현까지 해보고 싶습니다. 

### Step 1_ 애플리케이션을 위해 기본적인 to-do list 생각하기 
: 수입(income), 지출(expenses)의 목록과 금액을 적고 버튼을 클릭하면 UI추가, 계산 등이 일어납니다. 

##### 01) Add event handler 
(버튼용) 이벤트 핸들러를 추가합니다. 

##### 02) Get input values
입력창의 값을 받습니다.

##### 03) Add the new item to our data structure
데이터 구조에 새 아이템이 추가됩니다.

##### 04) Add the new item to the UI.
UI(User Interface)에도 추가됩니다.

#### 05) Calculate budget
예산을 계산합니다.

#### 06) Update the UI. 
UI(User Interface)에도 추가됩니다.

### Step 2_ 코딩 전에 코드를 구성하는 방법에 대한 고찰 - 모듈(Modules)

- 모듈은 강력한 애플리케이션 설계의 핵심 요소입니다. 
- 프로젝트의 코드 단위를 깔끔하게 분리하고 체계적으로 해줍니다. 
- 캡슐화(encapsulate)하여 일부 데이터를 외부에서 접근하지 못하게(private)하고, 
다른 데이터는 외부에서 접근가능(public)하게 합니다. 

이러한 개념은 프로젝트가 클수록 중요해집니다. 
기본적으로, 모듈은 코드를 논리적인 부분으로 나누고, 서로 상호작용(interact)하도록 해줍니다.

##### 이 프로젝트에서는 모듈을 어떻게 나눌 것인가?

| UI Module | Data Module | 
| :----- | :----- |
|02) Get input values||
|04) Add the new item to the UI.|03) Add the new item to our data structure|
|06) Update the UI|05) Calculate budget|

| Controller Module |
| :----- |
|01) Add event handler |

### Step 3_ 모듈패턴(Module Patten)
JavaScript의 인기있는 패턴 중 하나인 모듈패턴 방식으로 개발하고자 합니다. 

##### 관련 포스팅 : [모듈패턴(Module Patten)](https://sharryhong.github.io/2017/01/16/javascript-module-patton/)
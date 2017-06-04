---
title: portfolio-sli.do 서비스 (AngularJS)
date: 2016-12-12 20:23:57
categories: [Portfolio, Portfolio]
tags: [Portfolio, AngularJS, JavaScript, SASS, Gulp, sli.do]
---

## [Hong's portfolio - sli.do 바로가기](https://sharryhong.github.io/hs_slido/src)
[Github 소스 바로가기](https://github.com/sharryhong/TIL/tree/master/angularjs/hs_slido)

#### 포트폴리오 주제
강의 중 실시간으로 질문, 답변을 받는 서비스

![sli.do service](/image/slido-main.jpg)

#### 포트폴리오 개발 기간
2016-11 ~ 공부하며 코드 리펙토링 중입니다.

#### 특징 및 기능 
`반응형 웹` : 데스크탑, 테블릿, 모바일에 대응하여 적절한 view를 보여줍니다.
`JSON파일의 data`를 불러옵니다. (그룹 이름, 작성자 이름, 질문 내용, 좋아요 개수 등)
질문을 입력받아 `popular(인기순)`, `Recent(최신순)` 대로 보여줍니다.
popular(인기순) : `좋아요` 버튼 클릭시 `자동으로 상단`으로 이동합니다.
질문자 이름을 입력하지 않을 시 `Anonymous(익명)`로 표시됩니다.
질문 내용을 클릭하면 상세페이지로 이동하여 `comment(덧글)`를 달 수 있습니다.
덧글 개수가 JSON data로 저장되어 main에서 숫자로 보여집니다.

#### 사용 Skill
JavaScript, AngularJS, JSON, jQuery
HTML, SASS to CSS
Gulp

#### 주제 선정 이유
AngularJS로 서비스를 만들어보고 싶던 중, 생활코딩 세미나에서 [sli.do의 서비스](https://app.sli.do/event/qao1egje/ask)를 사용하였습니다.
사용이 직관적이어서 좋았고, 강의 중 질문을 바로 올리고, 나중에 강사가 모아서 대답을 할 수 있는 좋은 서비스라 생각되어 개발해보고 싶었습니다.

#### 고려사항
comment 기능이 있으면 좋을 것 같아 추가하였습니다.
JavaScript prototype Class문법
크로스 브라우징 : IE9이상

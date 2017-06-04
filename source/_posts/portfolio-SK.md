---
title: portfolio-SK 주식회사 사이트
date: 2016-11-25 14:40:43
categories: [Portfolio, Portfolio]
tags: [Portfolio, HTML, CSS, JavaScript, jQuery]
---

[Hong's portfolio - SK 주식회사 main 바로가기](http://sharry.dothome.co.kr/2016/hs-sk/index.html)
[sub page01](http://sharry.dothome.co.kr/2016/hs-sk/introduce_01.html) | [sub page02](http://sharry.dothome.co.kr/2016/hs-sk/business_01.html) | [sub page03-게시판리스트](http://sharry.dothome.co.kr/2016/hs-sk/prcenter_01.html) | [sub page04-게시판내용](http://sharry.dothome.co.kr/2016/hs-sk/prcenter_01_view.html)

![SK 주식회사 사이트](/image/sk.jpg)

#### 포트폴리오 개발 기간
2015-11

#### 특징 및 기능
`반응형 웹` : 데스크탑, 테블릿, 모바일에 대응하여 적절한 view를 보여줍니다.
`웹표준`, `웹접근성` 준수
크로스 브라우징 : `IE8` 이상

#### 사용 Skill
HTML, CSS, jQuery, JavaScript, Photoshop

#### 고려사항
디자인대로 마크업, 의미있는 마크업을 하기 위해 노력하였습니다.
개발단계를 고려하여 예상 가능한 부분을 미리 마크업하였습니다.(예 : 게시판의 제목이 길어질 경우)
버튼, 게시판 등은 모듈화하여 재사용성을 높였습니다.

> 2016년 12월 현재.. **코드 리펙토링**하면 좋을 것들
반응형을 위한 미디어쿼리를 `<head>`에서 `<link media..>`로 설정하였는데, 이럴 경우 성능에 좋지 않는 다는 것을 알게되었습니다.
이 부분을 **css상에서 @media**로 코드 리펙토링 하는 게 좋을 것 같습니다.

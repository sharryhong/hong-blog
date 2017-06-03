---
title: 2016 정보접근성 기술 컨퍼런스 & WAI-ARIA
date: 2016-12-13 13:31:01
categories: [Front-End, 웹접근성]
tags: [웹접근성, WAI-ARIA]
---

{% asset_img aria.jpg [ 소중하다! :) ] %}

12월 9일 금요일. **UN 인권의 날 기념 - 2016 정보접근성 기술 컨퍼런스**에 다녀왔습니다. 
집에서 먼 거리에 있어 상암쪽은 살면서 두번째네요~ 
결론은.. 눈 비비며 먼 길 다녀온 보람이 있었다는 것입니다. ^^

특히 우리 프론트엔드 개발스쿨의 **야무쌤** 파트였던 WAI-ARIA부분은 예전부터 알고 싶던 기술이었기 때문에 더 귀를 쫑끗하며 들었습니다. 
한국 웹접근성 지침을 잘 따르더라도, 모두가 동등하게 사용하는데에는 부족하다는데요. 
실제로 스크린리더기 등으로 들어보니 우리가 의도한 바를 어떤 분들은 알기 어렵구나, 그리고 아리아를 적용하는게 생각보다 어렵진 않겠구나를 느꼈습니다. 

> WAI-ARIA란?
접근성이 떨어지기 쉬운 **동적 컨텐츠에 접근성을 보완**하는 기술입니다. 

### 접근성이 떨어지기 쉬운 부분은?
동적인 웹 애플리케이션 접근성 보장을 위한 지침이 부족합니다.
Ajax를 통한 실시간 변경 콘텐츠를 못 읽을 수 있습니다.
페이지 콘텐츠 중 일부만 변경 시, 동일한 내용을 계속 읽어야 하는 문제가 발생합니다. 
화면을 확대해서 보는 분들의 경우, 가시범위 밖의 콘텐츠 변경 내용을 알기 어렵습니다. 
그 외에도 많다고 하네요 ㅜㅜ 

> WAI-ARIA의 목적?
마크업에 `역할(Role)`, `속성(Property)`, `상태(State)` 정보를 추가하여
**스크린 리더** 및 **보조 기기**등에서 **접근성 및 상호운용성**을 향상시키고
보다 나은 **사용자경험**(UX)을 제공하기 위함 

[브라우저 지원현황](http://caniuse.com/#search=wai-aria) 
: IE11부터, 대부분의 브라우저가 지원하고 있습니다. 

[WAI-ARIA 사례 바로가기](https://github.com/niawa/ARIA)
: 야무쌤 포함 여러 전문가들의 노력으로 아리아 사례가 github에 공개되어 있습니다. 

#### 세미나 그 후 나의 생각 
아직 공공기관이나 대기업의 사이트 정도만 웹접근성을 잘 따르려 노력하고 있다고 들었는데, 앞으로는 모두를 위해 천천히라도 적용하였으면 좋겠습니다. 
웹 접근성을 지키면 사람의 일부가 아니라, 전체에 좋아질거라 생각됩니다. 
노인을 위한 디자인을 위해, 3년간 노인 분장을 하고 도시를 돌아다녔던 [패트리샤 무어의 이야기](http://m.post.naver.com/viewer/postView.nhn?volumeNo=3353175&memberNo=22225909&vType=VERTICAL).. 그 결과 힘이 약한 노인이나 아이들 뿐 아니라, 모두에게 편리한 제품을 디자인할 수 있었습니다. 
웹, 앱도 다르지 않을거라 생각됩니다. 좋은 서비스에 맞는 좋은 접근성을 제공하여 누구나 쉽고 편리하게 사용하는 서비스를 만들고 싶네요... ^^ 

### 연관 링크
[W3C의 WAI-ARIA 1.1](https://www.w3.org/TR/wai-aria-1.1/)
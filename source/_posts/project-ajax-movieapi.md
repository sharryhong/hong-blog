---
title: Movie 박스오피스 - AJAX, Movie API
date: 2016-12-31 01:12:57
categories: [Portfolio, Free Project]
tags: [AJAX, 영화 API, JSON]
---

[결과화면 보기](https://sharryhong.github.io/javascript/05_AJAX/ajax-json-movieapi.html)

![결과 이미지](/image/movie.jpg)

### 박스오피스 사이트 : AJAX 통신, Movie API 사용

> 2017-01-04 코드 리펙토링 : 익스플로러(IE)에서는 for of문이 인식되지 않아 일반 for문으로 처리하였습니다. 하단에 설명 추가

### 특징 및 기능
1) [영화진흥위원회가 제공하는 **영화 API**사용](http://www.kobis.or.kr/kobisopenapi/homepg/main/main.do)
: 로컬 서버에서는 구현이 잘 되고 있으나 github의 gh-pages에서는 API data가 불러와 지지 않습니다. 그래서 2016-12-19일 기준으로 JSON파일을 만들어 연결하였습니다.

2) **[AJAX 비동기 통신 사용](https://sharryhong.github.io/2016/12/29/javascript-ajax)**

3) template 동적 생성

4) 랭킹 1~3위는 빨강배경, 4~10위는 회색배경 적용

5) 순위 변경 data가 0 일땐 `녹색 -` 표시, 순위 상승시 `빨강 화살표`, 순위 하락시 data 중 마이너스 삭제하고 `파랑 화살표` 표시

추가 예정 : 영화 상세 페이지
디자인 : CGV사이트 참고
영화 포스터 : API에서 제공하지 않아 못 넣었습니다. 아쉽네요 ㅜㅜ

### 코드 설명

1) AJAX관련 코드 : [자세한 설명은 여기에서](https://sharryhong.github.io/2016/12/29/javascript-ajax)

```
var xhr = new XMLHttpRequest();
xhr.open('GET', "http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=발급받은키&targetDt="+ today);
xhr.send();
```
제공하는 영화 API URL 맨 뒤에는 알고싶은 날짜를 적으면 됩니다. 저는 [Date() 클래스](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Date)를 사용하여 하루 전 날짜를 넣어주었습니다. (당일 날짜는 안되더군요.)

2) 하루 전 날짜 구하기

```
var d = new Date();
var yy = d.getFullYear();
var mm = d.getMonth() + 1;
var dd = d.getDate() - 1;
// var today = yy + "" + "" + mm + "" + dd;
// 혹은
var today = `${yy}${mm}${dd}`;
```

Date() 클래스의 인스턴스 d
d.getMonth() 리턴값은 0(1월) ~ 11(12월)

3) 랭킹 1~3위는 빨강배경, 4~10위는 회색배경 적용

```
var rank_array = document.querySelectorAll('.rank');
var gray_array = Array.prototype.slice.apply(rank_array);
var gray_rank = gray_array.slice(3);
for(var i=0; i<gray_rank.length; i++){
	gray_rank[i].classList.add('gray');
}
```

`<strong class="rank">'+'No.'+movie.rank+'</strong>'` 전체를 유사배열로 받아옵니다.
이 것을 `Array.prototype.slice.apply(rank_array);`로 실제 배열처럼 사용할 수 있게 합니다.
`.slice(3)`은 네번째 배열값부터 끝까지 적용한다는 뜻입니다.
즉, 이 코드는 `class="rank"`를 가진 전체 요소 중에 네번째 배열값부터 끝까지 class="gray"를 추가시킨다. 는 것인데 css상에는 아래처럼 되어있어 자동으로 회색배경이 적용됩니다.
```
.movie-contents .rank.gray{
	background: #555;
}
```

### 전체 코드

```
(function(global, XHR){
	'use strict';

	var createXHR = (function() {
		XHR = XHR || ActiveXObject('Microsoft.XMLHTTP');
		return function() {
			return new XHR;
		};
	})();

	var xhr = createXHR();
	var result_view = document.querySelector('.ajax-result');

	//오늘 날짜
	var d = new Date();
	var yy = d.getFullYear();
	var mm = d.getMonth() + 1;
	var dd = d.getDate() - 1;
	var today = `${yy}${mm}${dd}`;

	xhr.open('GET', "http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=발급받은키&targetDt="+ today);
	xhr.send();

	xhr.onreadystatechange = function() {
		if ( this.status === 200 && this.readyState === 4 ) {
			console.log('통신 데이터 전송 성공! ^^');
			// console.log(this.response);
			// text file
			var getmovies = this.response;
			var template = '';
			// text -> object
			getmovies = JSON.parse(getmovies);
			// json파일내에 있는 속성 results
			var movies = getmovies.boxOfficeResult.dailyBoxOfficeList;
			// movies 반복 순환 처리
			for(var movie of movies) {
				template += [
					'<li class="movie-contents">',
						'<strong class="rank">'+'No.'+movie.rank+'</strong>',
						'<h3 class="name">'+movie.movieNm+'</h3>',
						'<p class="opendt small">'+'개봉일 : '+'<span>'+movie.openDt+'</span>'+'</p>',
						'<p class="audiacc small">'+'누적 관객 수 : '+'<span>'+movie.audiAcc+'</span>'+'명'+'</p>',
						'<p class="rankinten small">'+'순위 변화 : '+'<span class="rank-change">'+movie.rankInten+'</span>'+'</p>',
					'</li>'
				].join('');
			}
		} else {
			console.log('통신 데이터 전송 실패');
		}
		result_view.innerHTML = template;

		// 랭킹 4위부터 회색배경
		var rank_array = document.querySelectorAll('.rank');
		var gray_array = Array.prototype.slice.apply(rank_array);
		var gray_rank = gray_array.slice(3);
		for(var i=0; i<gray_rank.length; i++){
			gray_rank[i].classList.add('gray');
		}
		// 순위변경 표시하기
		var rankinten_array = document.querySelectorAll('.rank-change');
		for(var a=0; a<rankinten_array.length; a++){
			var rankinten_el = rankinten_array[a];
			var rankinten_el_first = rankinten_el.firstChild;
			// console.log(rankinten_el_first.nodeValue);
			// 순위변경이 없다면 숫자 0을 없애고 css에 적용한 zero클래스 붙이기
			if(rankinten_el_first.nodeValue == 0){
				rankinten_el_first.nodeValue = '';
				rankinten_el.classList.add('zero');
			}
			// 순위가 올랐다면 css에 적용한 up클래스 붙이기
			else if(rankinten_el_first.nodeValue > 0){
				rankinten_el.classList.add('up');
			}
			// 순위가 내려갔다면 css에 적용한 down클래스 붙이기, 마이너스 없애기
			else if(rankinten_el_first.nodeValue < 0){
				// console.log(rankinten_el_first.nodeValue[0]);
				var el_value = rankinten_el_first.nodeValue;
				var result = el_value.slice(1)+el_value.slice(2, el_value.length);
				// console.log(result);
				rankinten_el_first.nodeValue = result;
				rankinten_el.classList.add('down');
			}
		}
	}

})(this, this.XMLHttpRequest);
```

### IE에서 작동되지 않는 문제점 발견
크롬에서 작업하고 크로스브라우징을 위해 모바일과 IE, 엣지에서 확인해보니 IE에서는 실행이 되지 않았습니다.
여러가지 분석 결과 for of문이 인식되지 않는 것을 알았고, json data 객체를 불러들이기 위해 for of문 대신 일반 for문을 사용하였습니다.

코드 리펙토링 부분
```
for(var i=0; i<movies.length; i++) {
	template += [
		'<li class="movie-contents">',
			'<strong class="rank">'+'No.'+movies[i].rank+'</strong>',
			'<h3 class="name">'+movies[i].movieNm+'</h3>',
			'<p class="opendt small">'+'개봉일 : '+'<span>'+movies[i].openDt+'</span>'+'</p>',
			'<p class="audiacc small">'+'누적 관객 수 : '+'<span>'+movies[i].audiAcc+'</span>'+'명'+'</p>',
			'<p class="rankinten small">'+'순위 변화 : '+'<span class="rank-change">'+movies[i].rankInten+'</span>'+'</p>',
		'</li>'
	].join('');
}
```

### 연관 링크
[영화진흥위원회 API](http://www.kobis.or.kr/kobisopenapi/homepg/main/main.do)

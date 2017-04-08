---
title: Photo Gallery - AJAX, JSON data
date: 2017-01-10 15:33:31
categories: [Portfolio, Free Project]
tags: [Gallery, AJAX, JSON]
---

### 사진 갤러리 : JavaScript, AJAX, JSON, CSS3 

[결과화면 보기](https://sharryhong.github.io/javascript/06_image_gallery/)
[해당 소스 보기](https://github.com/sharryhong/javascript/tree/master/06_image_gallery)

{% asset_img photo.jpg [결과 이미지] %}

> Window10의 기본 사진 애플리케이션 기능을 웹버전으로 만들어보는 작은 프로젝트입니다. :) 

### 특징 및 기능
1) AJAX로 JSON data 불러오기
2) JSON photo개수에 맞는 template 동적 생성
3) hover, focus시 CSS3 transform, transition 사용
4) 사진 click시 중앙에 확대, 확대시 검정배경 높이만큼 나오기 
5) 슬라이드 쇼 버튼 클릭시 슬라이드 쇼 재생, 다시 클릭시 멈추는 기능 
6) 슬라이드 쇼 재생시 사진을 클릭하면 재생이 끝나는 기능 

### 주요 코드 

#### 1) [AJAX로 JSON data 불러오기](https://sharryhong.github.io/2016/12/29/javascript-ajax/) 
```
var xhr = new XMLHttpRequest();
xhr.open("GET", "./data/gallery.json");
xhr.send();
xhr.onreadystatechange = function() {
  if(this.status === 200 && this.readyState === 4) {
    var data = JSON.parse(this.response);
      var template = '';
      var photos = data.results;
```
`gallery.json` 파일 내부의 `results` 배열객체 값을 변수 photos에 저장합니다. 

#### 2) JSON의 photos 개수만큼 template 동적 생성 

index.html `<ul class="ajax-result"></ul>` 내부에 
```
for(var i=0; i<photos.length; i++){
  template += [
    '<li>',
      '<a href="javascript:;" class="photo-link">',
        '<img class="photo-img" src="'+photos[i].image+'" alt="'+photos[i].alt+'">',
      '</a>',
    '</li>'
  ].join('');
}

result_view.innerHTML = template;
```
처음에 저장했던 `photos` 변수에 담긴 JSON data의 갯수만큼 template을 생성하여 뿌려줍니다. 

#### 3) CSS3 transform, transition, animation 
```
// transition을 주어 애니메이션 효과를 냅니다. 
.photo-link{
	position: static;
	display: inline-block;
	overflow: hidden;
	transition: .3s all ease-in-out;
}
.photo-img{
	display: inline-block;
	vertical-align: middle;
	transition: .5s all ease-in-out; /* vendorless fallback */
	-o-transition: .5s all ease-in-out; /* opera */
	-ms-transition: .5s all ease-in-out; /* IE 10 */
	-moz-transition: .5s all ease-in-out; /* Firefox */
	-webkit-transition: .5s all ease-in-out; /*safari and chrome */
}

// 사진 hover, focus시 약간 확대됩니다. 
.photo-link:hover .photo-img,
.photo-link:focus .photo-img {
	transform: scale(1.1);
}

// 사진 클릭시 JavaScript에서 class="on"이 추가되어 아래 style이 적용됩니다. 
.photo-link.on{
	position: absolute;
	z-index: 90;
	top: 0;
	left: 0;
	width: 100%;
	height: inherit;
	animation: ani-opacity 1s;
}
.photo-link.on .photo-img{
	width: 100%;
	height: 100%;
}

// CSS Animation
@keyframes ani-opacity {
	0% { 
		opacity: 0; 
	}
	100% { 
		opacity: 1; 
	}
}

// 클릭된 사진을 제외한 사진은 안보이게 하는 class="off" style입니다. 
.photo-link.off{
	display:none;
}
```

#### 4) 사진 click시 중앙에 확대, 확대시 검정배경 높이만큼 나오기

##### 검정배경에 관한 코드 
```
// 검정배경 Div요소 만들기 
var photoGallery = document.querySelector('.photo-gallery').firstElementChild;
var menuCoverDiv = document.createElement('div');
menuCoverDiv.setAttribute('class', 'menu-cover');
// 검정 배경 나오게 하기 
function menuCover(el) {
	// 목표노드.부모노드.insertBefore(insert삽입할노드, target목표노드)
	photoGallery.parentNode.insertBefore(menuCoverDiv, photoGallery);
	// 확대된 사진의 height
	var photoHeight = el.offsetHeight;
	// 사진크기와 브라우저크기를 비교하여 검정 배경 height 정하기
	if((windowHeight-90) > photoHeight){
		menuCoverDiv.style.height = (windowHeight-10)+'px';
	}else{
		menuCoverDiv.style.height = (photoHeight+30)+'px';
	}
}
// 검정 배경 없애기 
function removeMenuCover() {
	photoGallery.parentNode.removeChild(menuCoverDiv);
}
```

##### 사진 클릭시 확대되는 코드 
```
// 각 사진 클릭시 photoShow 함수 실행 
function photoAddEvent() {
	for(var i=0; i<photoLink.length; i++){
		photoLink[i].addEventListener("click", photoShow, false);
	}
}
// 사진 클릭시 커지는 함수 
function photoShow() {
	console.log("photoShow함수실행");
	// 현재 사진 
	index = photoLink.indexOf(this);
	// 현재 사진 제외하고 안보이게 처리 
	for(var j=0; j<photoLink.length; j++){
		if( j !== index ) {
			photoLink[j].classList.toggle("off");
		}
	}
	// 현재 사진 확대 
	this.classList.toggle("on");
	if(!photoClick){
		menuCover(this);
		photoClick = !photoClick;
		console.log('사진 클릭');
	}else{
		removeMenuCover();
		photoClick = !photoClick;
		index = 0;
		console.log('사진 클릭해제');
	}
}
```

#### 5) 슬라이드 쇼 버튼 클릭시 슬라이드 쇼 재생, 다시 클릭시 멈추는 기능
#### 6) 슬라이드 쇼 재생시 사진을 클릭하면 재생이 끝나는 기능
```
// 슬라이드 쇼를 멈추고 사진들이 원래대로 돌아오게 하는 함수 
function stopSlideShow(e){
	console.log("stopSlideShow함수실행");
	// 슬라이드 버튼이 눌러졌다면 
	if(chkBtn || PauseBtnOn){
		photoLink[index].classList.remove("on");
	}else{
		photoLink[index-1].classList.remove("on");
	}
	index = 0;
	clearInterval(slideInterval);
	photoAddEvent();
	removeMenuCover();
	slideBtn.classList.remove("pause-interval");
	slideBtn.classList.remove("on");
	for(var j=0; j<photoLink.length; j++){
		photoLink[j].classList.remove("off");
	}
	chkBtn = false;
	PauseBtnOn = false;
	photoClick = false;
	removeStopSlideShow();
}
// stopSlideShow함수 removeEvent
function removeStopSlideShow(){
	for(var j=0; j<photoLink.length; j++){
		photoLink[j].removeEventListener("click", stopSlideShow, false);
	}
}
// 슬라이드 쇼 함수
function slideShow() {
	for(var j=0; j<photoLink.length; j++){
		// 슬라이드 쇼 함수 진행 중 확대된 사진을 클릭하면 슬라이드 쇼 멈추기 
		photoLink[j].addEventListener("click", stopSlideShow, false);
		if( j !== index ) {
			photoLink[j].classList.add("off");
		}
	}
	photoLink[index].classList.add("on");
	menuCover(photoLink[index]);
	global.slideInterval = setInterval(function(){
		index++;
		if(index < photoLink.length){
			photoLink[index-1].classList.remove("on");
			photoLink[index-1].classList.add("off");
			photoLink[index].classList.remove("off");
			photoLink[index].classList.add("on");
			menuCover(photoLink[index]);
			console.log(index);
		}else { // 슬라이드 쇼 끝난 후 
			chkBtn = false;
			PauseBtnOn = false;
			photoClick = false;
			stopSlideShow();
		}
	}, 2000);
}
// 슬라이드 버튼 클릭시 
slideBtn.onclick = function(){
	// 슬라이드 재생 
	if(!chkBtn){
		slideShow();
		photoRemoveEvent();
		slideBtn.classList.remove("pause-interval");
		slideBtn.classList.add("on");
		chkBtn = true;
	}else{ // 슬라이드 멈춤 
		clearInterval(global.slideInterval);
		slideBtn.classList.remove("on");
		slideBtn.classList.add("pause-interval");
		chkBtn = false;
		PauseBtnOn = true;
	}
}
```


## 모바일 웹 프로젝트 O'kitchen

<image width= "100%" src= "mdimg/main.png">
Swiper.js 슬라이더와 Google Maps API 연동을 핵심으로 구현된 프로젝트입니다.<br>
모바일 환경에 최적화된 반응형 웹 디자인으로 사용자 인터랙션과 동적인 콘텐츠 표시에<br>중점을 두었습니다.





## 📌 주요기능
- 모바일 메뉴 토글 시스템 (모바일 텝 구현)
- Swiper.js를 활용한 슬라이더 구현 (메인/서브 슬라이더로 컨텐츠 동적으로 표시)
- Google Maps API 연동
- 반응형 웹 디자인 (모바일 / 데스크탑 구분)

## 🛠 사용 기술
| 기술 | 설명 |
| --- | --- |
| ![HTML](https://img.shields.io/badge/-HTML-F05032?style=flat-square&logo=html5&logoColor=ffffff) | HTML5 마크업 구조 |
| ![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-square&logo=css3&logoColor=white) | CSS3 반응형 스타일 처리 |
| ![javascript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-square&logo=javascript&logoColor=white) | DOM 제어 및 외부 라이브러리 연동 |
| [![Swiper](https://img.shields.io/badge/Swiper-6332F6?style=for-the-square&logo=swiper&logoColor=white)](https://swiperjs.com/) |  슬라이더 라이브러리
| ![Google Maps](https://img.shields.io/badge/Google%20Maps-4285F4?style=for-the-square&logo=google-maps&logoColor=white) |  특정 좌표의 지도를 표시


## 🧩 기능 상세 설명

### ✅ 반응형 메뉴 구현
- 모바일 환경에서 상단의 'tab' 버튼 클릭 시 사이드 메뉴 열림
- 메뉴가 열리면 스크롤이 비활성화, 배경 콘텐츠 고정
- 오버레이(dim) 영역을 클릭하거나 메뉴 내의 '닫기' 버튼을 누르면 메뉴 닫힘, 스크롤 다시 활성화

```js
window.addEventListener("load", function(){
	let mobile=document.querySelector("#mobile");
	let tab=document.querySelector("#header .tab");
	let dim=document.querySelector(".dim");
	let closeBtn=document.querySelector(".icon .close");

	tab.addEventListener("click", function(e){
		e.preventDefault();

		document.body.classList.add("fixed");
		mobile.classList.add("active");
		dim.classList.add("active");
	});

	dim.addEventListener("click", function(){
		document.body.classList.remove("fixed");
		mobile.classList.remove("active");
		dim.classList.remove("active");
	});

	closeBtn.addEventListener("click", function(e){
		e.preventDefault();

		document.body.classList.remove("fixed");
		mobile.classList.remove("active");
		dim.classList.remove("active");
	});
});
```
<figure class="third"  >
<image width= "30%" src= "mdimg/mobile1.png">
<image width= "30%" src= "mdimg/mobile2.png">
<image width= "30%" src= "mdimg/mobile3.png">
<image width= "30%" src= "mdimg/mobile4.png">
<image width= "30%" src= "mdimg/mobile5.png">
</figure>

### ✅ 메인 Swiper

- Swiper.js 라이브러리를 활용하여 이미지와 콘텐츠를 동적으로 전환
- 분수형 페이지네이션 기능을 제공 (현재 슬라이드 번호와 전체 슬라이드 수를 표시)
```js
window.addEventListener("load", function(){
	const mainSwiper=new Swiper("#main_slider .swiper-container", {
		navigation: {
			prevEl: "#main_slider .swiper-button-prev",
			nextEl: "#main_slider .swiper-button-next"
		},
		pagination: {
			el: "#main_slider .swiper-pagination",
			type: "fraction"
		}
	});
});
```
<image width= "100%" src= "mdimg/mainslider.png">

### ✅ 다중 Swiper

-  Swiper.js를 활용하여 다중 슬라이드 뷰를 구현, 사용자 스크롤 기반의 콘텐츠 탐색 제공
- breakpoints 설정을 통해 뷰포트 640px 이상에서 slidesPerView 값을 동적으로 조정, 반응형 디스플레이 최적화 제공
```JS
window.addEventListener("load", function(){
	const subSwiper=new Swiper("#sub_slider .swiper-container", {
		slidesPerView: 1.5,
		spaceBetween: 10,
		breakpoints: {
			640: {
				slidesPerView: 3.5,
				spaceBetween: 5
			}
		}
	});
});
```

<image width= "100%" src= "mdimg/subslider.png">


### ✅  Google Maps API 연동
- Google Maps JavaScript API를 활용하여 지정된 위도 및 경도 지점에 지도 임베드, 커스텀 마커 표시
- 특정 목적에 맞게 지도 시각화를 최적화
```js
let map;

function initMap(){
	let myLatLng={lat: 37.390141551118695, lng: 126.97151846772532};

	let map=new google.maps.Map(document.getElementById("map"), {
		center: myLatLng,
		zoom: 16,
		mapTypeControl: false,
		zoomControl: false,
		fullscreenControl: false,
		rotateControl: false
	});

	let marker=new google.maps.Marker({
		position: myLatLng,
		map: map,
		title: "(주)오뚜기"
	});
}
```
<image width= "100%" src= "mdimg/googlemap.png">




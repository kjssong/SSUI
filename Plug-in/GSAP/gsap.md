# **GSAP (GreenSock Animation Platform)**

https://greensock.com/gsap/

웹 화면에 쉽게 사용할 수 있는 타임라인 기반 애니메이션 자바스크립트 라이브러리  
<br/>

-------------

<br/>

## GSAP 가져오기<br/>

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
```
<br/>

------------

<br/>

## 사용방법

```js
// gsap_01.html

// to : 시작 -> 끝
gsap.to('.bg-box > div', {
    rotation: 360, // 회전
    x: 500, // x축으로 이동
    duration: 2 // 지속시간
});

// from : 끝 -> 시작
gsap.from('.bg-box > div', {
    rotation: 360, // 회전
    x: 500, // x축으로 이동
    duration: 2 // 지속시간
});

// fromTo : 시작 <-> 끝
gsap.fromTo('.bg-box > div', {
    rotation: 0, // 회전
    x: 0, // x축으로 이동
},
{
    rotation: 360, // 회전
    x: 500, // x축으로 이동
    duration: 2 // 지속시간
});
```
```js
// gsap_02.html

// 제어
let gsapControl = gsap.to('.bg-box > div', {
    rotation: 360, // 회전
    x: 300, // x축으로 이동
    duration: 3 // 지속시간
});

gsapControl.play();
gsapControl.pause();
gsapControl.seek(3);
.
.
.
```
```js
// gsap_03.html

// timeline : 순서대로 진행
	let tl = gsap.timeline({});

	tl.to('._bg01', {
		rotation: 360, // 회전
		x: 500, // x축으로 이동
		duration: 2 // 지속시간
	})
	.to('._bg02', {
		rotation: 360, // 회전
		x: 500, // x축으로 이동
		duration: 2 // 지속시간
	})
	.to('._bg03', {
		rotation: 360, // 회전
		x: 500, // x축으로 이동
		duration: 2 // 지속시간
	});
```
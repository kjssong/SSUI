# **Smooth Scrollbar**

https://idiotwu.github.io/smooth-scrollbar/

스크롤 부드럽게 하는 플러그인
<br/>

-------------

<br/>

## Smooth Scrollbar 가져오기<br/>

```html
<script src="https://unpkg.com/smooth-scrollbar@latest/dist/smooth-scrollbar.js"></script>
```
<br/>

------------

<br/>

## 사용방법

```js
// smooth_scrollbar_01.html

var Scrollbar = window.Scrollbar;

Scrollbar.init(document.querySelector('#wrap'), {
	damping: 0.1
});
```

```js
// Smooth Scrollbar + GSAP
// smooth_scrollbar_02.html

gsap.registerPlugin(ScrollTrigger); // 스크롤 플러그인 안정화?

const Scrollbar = window.Scrollbar;
const scroller = document.querySelector('#wrap');

const scBar = Scrollbar.init(scroller, {
	damping: 0.1
});

ScrollTrigger.scrollerProxy('#wrap', {
	scrollTop(value){
		if(arguments.length){
			scBar.scrollTop = value;
		}
		return scBar.scrollTop;			
	}		
});

scBar.addListener(ScrollTrigger.update);

ScrollTrigger.defaults({
	scroller: scroller
});

gsap.to('.txt1', {
	scrollTrigger: {
		trigger: '.sct01',
		start: '0 0',
		end: '+=3000',
		pin: true,
		scrub: 0.5,
		markers: true
	},
	scale: 10
});

gsap.to('.txt2', {
	scrollTrigger: {
		trigger: '.sct02',
		start: '0 0',
		end: '+=3000',
		pin: true,
		scrub: 0.5,
		markers: true
	},
	scale: 30
});
```
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
// smooth_scrollbar.html

var Scrollbar = window.Scrollbar;

Scrollbar.init(document.querySelector('#wrap'), {
	damping: 0.1
});
```
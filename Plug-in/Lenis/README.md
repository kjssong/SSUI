#  Lenis 스크롤 가이드

> 부드러운 관성 스크롤을 만들어주는 JavaScript 라이브러리 [Lenis](https://github.com/studio-freight/lenis)

Lenis는 브라우저의 기본 스크롤보다 훨씬 더 부드럽고 자연스러운 **transform 기반 관성 스크롤**을 제공합니다.

---

##  특징

- 한 박자 느린 부드러운 스크롤 애니메이션
- 휠 및 터치스크롤 자동 지원
- scrollTo 기능 내장
- GSAP ScrollTrigger와 완벽한 호환

---

## 설치

```html
<!-- CDN 버전 (권장) -->
<script src="https://cdn.jsdelivr.net/npm/@studio-freight/lenis@1.0.34/lenis.min.js"></script>

# 또는 NPM 설치
npm install @studio-freight/lenis
```

## 기본 사용법


```html
<div class="lenis">
  <div class="scroll-content">
    <!-- 여기에 스크롤될 콘텐츠 -->
  </div>
</div>
```
```js
const lenis = new Lenis({
  wrapper: document.querySelector(".lenis"),
  content: document.querySelector(".scroll-content"),
  lerp: 0.07,      // 낮을수록 더 천천히 따라옴 (관성)
  smooth: true     // 부드러운 스크롤 활성화
});

function raf(time) {
  lenis.raf(time);
  requestAnimationFrame(raf);
}
requestAnimationFrame(raf);
```



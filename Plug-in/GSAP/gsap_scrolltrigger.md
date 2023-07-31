# **GSAP - ScrollTrigger**
<br/>

스크롤시 해당 요소가 보이면 효과 발생

-------------

<br/>

## GSAP, ScrollTrigger 가져오기<br/>

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
```
<br/>

------------

<br/>

## 사용방법

```js
// gsap_scrolltrigger_01.html

// 기본
gsap.to('._bg01', {
    scrollTrigger: {
        trigger: '.sct01',
        start: '0% 0%', // start(시작) scroller-strat(시작 지점 선택)
        end: '+=3000', // end(종료) scroller-end(종료 지점 선택)
        pin: true, // 화면 고정
        scrub: false, // true, false, 숫자
        markers: true // 가이드 라인
    },
    x: 500,
    duration: 4
});	
```
```js
// gsap_scrolltrigger_02.html

// timeline : 순서대로 진행
let tl = gsap.timeline({
    scrollTrigger: {
        trigger: '.sct01',
        start: '0% 0%', // start(시작) scroller-strat(시작 지점 선택)
        end: '+=3000', // end(종료) scroller-end(종료 지점 선택)
        pin: true, // 화면 고정
        scrub: 0.5, // true, false, 숫자
        markers: true // 가이드 라인
    }
});

tl.to('._bg01', {
    x: 500,
    duration: 4
})
.to('._bg02', {
    x: 200,
    duration: 4
})
.to('._bg03', {
    x: 700,
    duration: 4
})
```
```js
// gsap_scrolltrigger_03.html

// 토글액션
gsap.to('.sct01', {
    scrollTrigger: {
        trigger: '.sct01',
        start: '20% 50%', // start(시작) scroller-strat(시작 지점 선택)
        end: '70% 50%', // end(종료) scroller-end(종료 지점 선택)
        markers: true, // 가이드 라인
        onEnter: function(){
            // 지정한 범위 안으로 내려갈때 호출
            document.querySelector('.gsap-txt').innerText = 'Enter';
        },
        onLeave: function(){
            // 지정한 범위 밖으로 내려갈때 호출 
            document.querySelector('.gsap-txt').innerText = 'Leave';
        },
        onEnterBack: function(){
            // 지정한 범위 안으로 올라갈때 호출
            document.querySelector('.gsap-txt').innerText = 'EnterBack';
        },
        onLeaveBack: function(){
            // 지정한 범위 밖으로 올라갈때 호출
            document.querySelector('.gsap-txt').innerText = 'LeaveBack';
        }
    }
});
```
```js
// gsap_scrolltrigger_03.html

// 스크롤매직처럼 쓰기
const scts = document.querySelectorAll('section');

for(let i = 0; i < scts.length; i++){
    gsap.to(scts[i], {
        scrollTrigger: {
            trigger: scts[i],
            start: '20% 50%', // start(시작) scroller-strat(시작 지점 선택)
            end: '70% 50%', // end(종료) scroller-end(종료 지점 선택)
            markers: true, // 가이드 라인
            onEnter: function(){
                // 지정한 범위 안으로 내려갈때 호출
                scts[i].classList.add('_motion_on');
            },
            onLeave: function(){
                // 지정한 범위 밖으로 내려갈때 호출 
                scts[i].classList.remove('_motion_on');
            },
            onEnterBack: function(){
                // 지정한 범위 안으로 올라갈때 호출
                scts[i].classList.add('_motion_on');
            },
            onLeaveBack: function(){
                // 지정한 범위 밖으로 올라갈때 호출
                scts[i].classList.remove('_motion_on');
            }
        }
    });
}
```
```js
// gsap_scrolltrigger_04.html

// addLabel : 그룹으로 묶어 실행
let tl = gsap.timeline({
    scrollTrigger: {
        trigger: '.sct01',
        start: '0% 0%', // start(시작) scroller-strat(시작 지점 선택)
        end: '100% 100%', // end(종료) scroller-end(종료 지점 선택)
        pin: false, // 화면 고정
        scrub: false, // true, false, 숫자
        markers: true // 가이드 라인
    }
});

tl
    .to('._bg01', {
        x: 500,
        duration: 1
    })
    .to('._bg02', {
        x: 300,
        duration: 1
    })

    .addLabel('groupA')
    .to('._bg03', {
        x: 500,
        duration: 1
    }, 'groupA')
    .to('._bg04', {
        x: 300,
        duration: 1
    }, 'groupA')

    .addLabel('groupB')
    .to('._bg05', {
        x: 200,
        duration: 1
    }, 'groupB')
    .to('._bg06', {
        x: 700,
        duration: 1
    }, 'groupB')

    .addLabel('groupC')
    .to('._bg07', {
        x: 800,
        duration: 1
    }, 'groupC')
    .to('._bg08', {
        x: 600,
        duration: 1
    }, 'groupC')
```
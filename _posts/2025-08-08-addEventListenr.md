---
layout: single
title: "addEventListener 완전 중요!!"
excerpt: "addEventListener는 완전 중요한 내용이므로 복습 또 복습하자."
categories: JavaScript
tag: JavaScript
toc: true
published: true
---

이번에 복습 할 내용은 진짜 중요한 내용이다.
그것은 바로 **addEventListener**이다.

## **addEventListener**
내가 이해한대로  **addEvenListener**에 대해 적어보자
그냥 설명하는것보다는 확실히 코드를 보면서 설명하는게 직관적이다.

```html
<body>

    <p class="content">본문1</p>
    <p class="content">본문2</p> 
    <div id="box" class="box">Event Listener</div>
    <div>
        <button id="btn-box">Opne btn</button>
    </div>

<script>
   document.getElementsByClassName(`content`)[0].addEventListener(`mouseover`, 
            function() {
                document.getElementsByClassName(`content`)[0].style.color = 'skyblue';
            }
        );
        document.getElementsByClassName(`content`)[0].addEventListener(`mouseleave`,
            function() {
                document.getElementsByClassName(`content`)[0].style.color = 'black'

            }
        );
        document.getElementsByClassName(`content`)[1].addEventListener(`click`, 
            function() {
                document.getElementsByClassName(`content`)[1].innerHTML = '변경완료';
            }
        );
</script>
</body
```
**document.getElementsByClassName('content')[0]**는   
클래스 이름이 **class = "content"**인 모든 요소를 가져온다.   
**[0]** 은 *class = "content"를 가진 **HTML코드**의** 첫번째 요소를 가리킨다.
위에코드에서는 <p class="content">본문1</p>를 가리킨다.

그 다음에  **addEventListener('mouseover', function())**이 나오는 걸 확인 할 수 있는데
바로 **addEventListener**의 문법이다.

**addEventListener** 는 이벤트 발생시 **콜백함수**를 수행한다.

위의 코드에서는 **function()**이 **콜백함수**다.

다음 제공된 코드에서는 다음과 같은 기능을 한다.

content 클래스를 가진 첫 번째 문단에 마우스를 올리면 글자 색이 하늘색으로,

마우스를 치우면 검정색으로 돌아오고,

두 번째 문단을 클릭하면 글자가 '변경완료'로 바뀌는 기능이다.













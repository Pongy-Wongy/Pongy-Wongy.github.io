```yaml
---
layout: single
title: "이미지 캐러셀과 탭 메뉴로 구현한 반응형 쇼핑몰 페이지"
excerpt: "이 코드는 Bootstrap과 CSS로 스타일링된 이미지 캐러셀과 탭 메뉴를 통해 상품을 카테고리별로 보여주는 반응형 쇼핑몰 페이지를 구현합니다. JavaScript로 캐러셀 자동 전환과 탭 전환, 구매 버튼 클릭 시 알림 기능을 추가했습니다."
categories: [HTML, CSS, JavaScript]
tag: [carousel, tab-menu, Bootstrap, HTML, CSS, JavaScript]
toc: true
published: true
---
```

# 이미지 캐러셀과 탭 메뉴로 구현한 반응형 쇼핑몰 페이지

이 코드는 이미지 캐러셀과 탭 메뉴를 사용해 상품을 카테고리별로 보여주는 간단한 쇼핑몰 페이지를 구현합니다. 사용자가 버튼을 클릭하거나 자동으로 전환되는 캐러셀과 탭 메뉴를 통해 상품을 쉽게 탐색할 수 있습니다.

---

## 💻 전체 코드

```html
<!-- 1. 캐러셀 섹션 -->
<div class="carousel-wrapper">
  <div class="text-center mt-4 mb-2">
    <h2>솔데스크</h2>
  </div>
  <div class="carousel" id="carousel">
    <div class="slide"><img src="../img/new_jeans01.png" alt="" /></div>
    <div class="slide"><img src="../img/new_jeans02.png" alt="" /></div>
    <div class="slide"><img src="../img/new_jeans03.png" alt="" /></div>
  </div>
  <div class="text-center my-2">
    <button class="btn btn-secondary" id="prev">이전</button>
    <button class="btn btn-secondary" id="next">다음</button>
  </div>
</div>

<!-- 2. 탭 메뉴와 상품 목록 -->
<div class="container">
  <h4 class="mt-4">카테고리</h4>
  <ul class="list">
    <li class="tab-button select">상의</li>
    <li class="tab-button">하의</li>
    <li class="tab-button">신발</li>
  </ul>
  <div class="tab-content show" id="content0">
    <div class="card">...</div>
    <!-- 상의 상품 카드 3개 -->
  </div>
  <div class="tab-content" id="content1">
    <div class="card">...</div>
    <!-- 하의 상품 카드 3개 -->
  </div>
  <div class="tab-content" id="content2">
    <div class="card">...</div>
    <!-- 신발 상품 카드 3개 -->
  </div>
</div>

<!-- 3. JavaScript 로직 -->
<script>
  const nextBtn = document.getElementById(`next`);
  const prevBtn = document.getElementById(`prev`);
  const slide = document.getElementById(`carousel`);
  let currentSlide = 1;

  nextBtn.addEventListener(`click`, next);
  prevBtn.addEventListener(`click`, prev);

  function next() {
    if (currentSlide == 1) {
      slide.style.transform = `translateX(-100vw)`;
      currentSlide = 2;
    } else if (currentSlide == 2) {
      slide.style.transform = `translateX(-200vw)`;
      currentSlide = 3;
    } else if (currentSlide == 3) {
      slide.style.transform = `translateX(0vw)`;
      currentSlide = 1;
    }
  }

  function prev() {
    if (currentSlide == 2) {
      slide.style.transform = `translateX(0vw)`;
      currentSlide = 1;
    } else if (currentSlide == 3) {
      slide.style.transform = `translateX(-100vw)`;
      currentSlide = 2;
    } else if (currentSlide == 1) {
      slide.style.transform = `translateX(-200vw)`;
      currentSlide = 3;
    }
  }

  let timeLeft = 5;
  setInterval(function () {
    timeLeft--;
    if (timeLeft <= 0) {
      next();
      timeLeft = 5;
    }
  }, 1000);

  const tabBtn = document.getElementsByClassName(`tab-button`);
  const tabContent = document.getElementsByClassName(`tab-content`);

  for (let i = 0; i < tabBtn.length; i++) {
    tabBtn[i].addEventListener(`click`, function () {
      for (let j = 0; j < tabBtn.length; j++) {
        tabBtn[j].classList.remove(`select`);
        tabContent[j].classList.remove(`show`);
      }
      tabBtn[i].classList.add(`select`);
      tabContent[i].classList.add(`show`);
    });
  }

  const buy = document.getElementsByClassName(`btn btn-sm btn-primary`);
  const title = document.getElementsByClassName(`card-title`);
  const price = document.getElementsByClassName(`card-text`);

  for (let i = 0; i < buy.length; i++) {
    buy[i].addEventListener(`click`, function (event) {
      const productTitle = title[i].textContent;
      const productPrice = price[i].textContent;
      alert(`\n${productTitle}\n${productPrice}\n`);
      event.preventDefault();
    });
  }
</script>
```

---

## ✨ 코드 로직 요약

이 코드는 세 가지 주요 기능을 구현합니다:

1. **이미지 캐러셀**: 화면 전체를 차지하는 이미지 슬라이드가 "이전", "다음" 버튼 클릭 또는 5초마다 자동으로 전환됩니다.
2. **탭 메뉴**: "상의", "하의", "신발" 탭을 클릭하면 해당 카테고리의 상품이 표시됩니다.
3. **구매 버튼**: 각 상품의 "구매" 버튼을 클릭하면 상품명과 가격이 알림창으로 표시됩니다.

---

## 🔍 코드 상세 설명

### 1️⃣ 첫 번째 부분: 이미지 캐러셀 구현

```html
<div class="carousel-wrapper">
  <div class="text-center mt-4 mb-2">
    <h2>솔데스크</h2>
  </div>
  <div class="carousel" id="carousel">
    <div class="slide"><img src="../img/new_jeans01.png" alt="" /></div>
    <div class="slide"><img src="../img/new_jeans02.png" alt="" /></div>
    <div class="slide"><img src="../img/new_jeans03.png" alt="" /></div>
  </div>
  <div class="text-center my-2">
    <button class="btn btn-secondary" id="prev">이전</button>
    <button class="btn btn-secondary" id="next">다음</button>
  </div>
</div>
```

- **💡 로직 설명**:  
  이 부분은 화면 전체를 차지하는 이미지 캐러셀을 구현합니다. `.carousel` 요소는 **flex** 레이아웃을 사용해 세 개의 슬라이드를 가로로 배열하고, CSS의 **transform: translateX**를 통해 슬라이드를 이동시킵니다. "이전"과 "다음" 버튼은 JavaScript로 제어되며, **Bootstrap**의 버튼 스타일을 사용해 깔끔한 UI를 제공합니다.

- **📘 문법 설명**:
  - **`<div class="carousel-wrapper">`**: 캐러셀 전체를 감싸는 컨테이너로, **overflow: hidden**을 통해 화면 밖의 슬라이드를 숨깁니다.
  - **`.carousel { display: flex; }`**: 슬라이드를 가로로 배열하기 위해 **flex** 레이아웃을 사용합니다.
  - **`.slide img`**: 이미지 크기를 **50vw**로 설정하고, **object-fit: cover**로 이미지가 왜곡되지 않도록 조정합니다.
  - **Bootstrap 클래스 (`btn btn-secondary`)**: Bootstrap의 스타일을 적용해 버튼을 꾸밉니다.

### 2️⃣ 두 번째 부분: 탭 메뉴와 상품 목록

```html
<div class="container">
  <h4 class="mt-4">카테고리</h4>
  <ul class="list">
    <li class="tab-button select">상의</li>
    <li class="tab-button">하의</li>
    <li class="tab-button">신발</li>
  </ul>
  <div class="tab-content show" id="content0">
    <div class="card">...</div>
    <!-- 상의 상품 카드 3개 -->
  </div>
  <div class="tab-content" id="content1">
    <div class="card">...</div>
    <!-- 하의 상품 카드 3개 -->
  </div>
  <div class="tab-content" id="content2">
    <div class="card">...</div>
    <!-- 신발 상품 카드 3개 -->
  </div>
</div>
```

- **💡 로직 설명**:  
  이 섹션은 "상의", "하의", "신발" 탭을 클릭하면 해당 카테고리의 상품 카드가 표시되는 탭 메뉴를 구현합니다. 기본적으로 "상의" 탭이 선택된 상태로 시작하며, 각 탭의 콘텐츠는 **display: none**과 **display: flex**를 통해 전환됩니다. 상품 카드는 **Bootstrap card** 컴포넌트를 활용해 이미지, 제목, 가격, 구매 버튼을 포함합니다.

- **📘 문법 설명**:
  - **`.tab-button`**: 탭 버튼에 적용된 스타일로, **float: left**를 사용해 가로로 배치합니다. 선택된 탭은 **.select** 클래스를 통해 상단에 노란색 테두리를 표시합니다.
  - **`.tab-content`**: 탭 콘텐츠는 기본적으로 **display: none**으로 숨겨져 있으며, **.show** 클래스가 추가되면 **display: flex**로 표시됩니다.
  - **`.card`**: Bootstrap의 카드 컴포넌트를 사용해 상품 정보를 깔끔하게 표시합니다. **object-fit: cover**로 이미지가 카드 크기에 맞게 조정됩니다.

### 3️⃣ 세 번째 부분: JavaScript 인터랙션

```javascript
const nextBtn = document.getElementById(`next`);
const prevBtn = document.getElementById(`prev`);
const slide = document.getElementById(`carousel`);
let currentSlide = 1;

nextBtn.addEventListener(`click`, next);
prevBtn.addEventListener(`click`, prev);

function next() {
  if (currentSlide == 1) {
    slide.style.transform = `translateX(-100vw)`;
    currentSlide = 2;
  } else if (currentSlide == 2) {
    slide.style.transform = `translateX(-200vw)`;
    currentSlide = 3;
  } else if (currentSlide == 3) {
    slide.style.transform = `translateX(0vw)`;
    currentSlide = 1;
  }
}

function prev() {
  if (currentSlide == 2) {
    slide.style.transform = `translateX(0vw)`;
    currentSlide = 1;
  } else if (currentSlide == 3) {
    slide.style.transform = `translateX(-100vw)`;
    currentSlide = 2;
  } else if (currentSlide == 1) {
    slide.style.transform = `translateX(-200vw)`;
    currentSlide = 3;
  }
}

let timeLeft = 5;
setInterval(function () {
  timeLeft--;
  if (timeLeft <= 0) {
    next();
    timeLeft = 5;
  }
}, 1000);

const tabBtn = document.getElementsByClassName(`tab-button`);
const tabContent = document.getElementsByClassName(`tab-content`);

for (let i = 0; i < tabBtn.length; i++) {
  tabBtn[i].addEventListener(`click`, function () {
    for (let j = 0; j < tabBtn.length; j++) {
      tabBtn[j].classList.remove(`select`);
      tabContent[j].classList.remove(`show`);
    }
    tabBtn[i].classList.add(`select`);
    tabContent[i].classList.add(`show`);
  });
}

const buy = document.getElementsByClassName(`btn btn-sm btn-primary`);
const title = document.getElementsByClassName(`card-title`);
const price = document.getElementsByClassName(`card-text`);

for (let i = 0; i < buy.length; i++) {
  buy[i].addEventListener(`click`, function (event) {
    const productTitle = title[i].textContent;
    const productPrice = price[i].textContent;
    alert(`\n${productTitle}\n${productPrice}\n`);
    event.preventDefault();
  });
}
```

- **💡 로직 설명**:  
  JavaScript는 캐러셀 이동, 탭 전환, 구매 버튼 동작을 제어합니다.

  - **캐러셀**: **next()**와 **prev()** 함수는 **transform: translateX**를 사용해 슬라이드를 이동시키고, **setInterval**로 5초마다 자동 전환됩니다.
  - **탭 메뉴**: **for** 루프를 사용해 각 탭 버튼에 클릭 이벤트를 추가하며, 클릭 시 기존 선택된 탭과 콘텐츠를 비활성화하고 새로운 탭을 활성화합니다.
  - **구매 버튼**: 클릭 시 상품명과 가격을 **alert**로 표시하며, **event.preventDefault()**로 기본 링크 동작을 방지합니다.

- **📘 문법 설명**:
  - **document.getElementById()**: 특정 ID를 가진 요소를 선택합니다.
  - **addEventListener()**: 버튼 클릭 같은 사용자 이벤트를 감지해 함수를 실행합니다.
  - **classList.add() / remove()**: 요소의 클래스를 동적으로 추가하거나 제거해 스타일을 변경합니다.
  - **setInterval()**: 일정 시간(1초)마다 코드를 실행해 캐러셀을 자동 전환합니다.
  - **event.preventDefault()**: `<a>` 태그의 기본 동작(페이지 이동)을 막습니다.

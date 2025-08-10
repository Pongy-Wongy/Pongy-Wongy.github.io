---
layout: single
title: "바닐라 JS로 간단 카페 키오스크 시스템"
excerpt: "바닐라 JS로 간단 카페 키오스크 시스템 "
categories: JavaScript
tag: JavaScript
toc: true
published: true
---

# 카페 주문 시스템: JavaScript로 구현한 간단한 주문 관리

이 코드는 HTML과 JavaScript를 사용해 카페 메뉴를 선택하고 주문 수량을 관리하며, 총 금액을 계산하고 주문을 확인하는 기능을 제공합니다.

---

## 💻 전체 코드

```javascript
// 1. 변수 선언 및 DOM 요소 선택
let count1 = 0;
let count2 = 0;
let count3 = 0;

const firstOrderBtn = document.getElementById(`orderBtn1`);
const secondOrderBtn = document.getElementById(`orderBtn2`);
const thirdOrderBtn = document.getElementById(`orderBtn3`);

const firstQuantity = document.getElementById(`quantity1`);
const secondQuantity = document.getElementById(`quantity2`);
const thirdQuantity = document.getElementById(`quantity3`);

// 2. 주문 처리 공통 함수
function handleOrder(orderButton, count, quantityDisplay) {
    count += 1;
    quantityDisplay.innerHTML = count;
    updateTotal();
    if (count === 5) {
        orderButton.disabled = true;
    }
    return count;
}

// 3. 각 메뉴의 주문 처리
firstOrderBtn.addEventListener('click', function() {
    count1 = handleOrder(this, count1, firstQuantity);
});

secondOrderBtn.addEventListener('click', function() {
    count2 = handleOrder(this, count2, secondQuantity);
});

thirdOrderBtn.addEventListener('click', function() {
    count3 = handleOrder(this, count3, thirdQuantity);
});

// 4. 총 금액 계산
function updateTotal() {
    let total = (count1 * 3000) + (count2 * 4000) + (count3 * 5000);
    document.getElementById(`totalAmount`).innerHTML = total;
}

// 5. 주문 초기화
document.getElementById(`resetBtn`).addEventListener(`click`, function () {
    count1 = 0;
    count2 = 0;
    count3 = 0;
    firstQuantity.innerHTML = 0;
    secondQuantity.innerHTML = 0;
    thirdQuantity.innerHTML = 0;
    firstOrderBtn.disabled = false;
    secondOrderBtn.disabled = false;
    thirdOrderBtn.disabled = false;
    updateTotal();
});

// 6. 주문 확인
document.getElementById(`confirmBtn`).addEventListener(`click`, function () {
    let orderText = `주문내역\n`;
    let total = 0;

    if (count1 > 0) {
        orderText += `아메리카노 ${count1}개 = ${count1 * 3000}원\n`;
        total += count1 * 3000;
    }

    if (count2 > 0) {
        orderText += `카페라떼 ${count2}개 = ${count2 * 4000}원\n`;
        total += count2 * 4000;
    }

    if (count3 > 0) {
        orderText += `케이크 ${count3}개 = ${count3 * 5000}원\n`;
        total += count3 * 5000;
    }

    orderText += `\n총 금액 : ${total}원`;
    alert(orderText);
});
```

---

## ✨ 전체 로직 요약

이 코드는 카페 주문 시스템을 구현합니다. 사용자가 메뉴(아메리카노, 라떼, 케이크)를 선택하면 주문 수량이 증가하고, 총 금액이 실시간으로 업데이트됩니다. 최대 5개까지 주문 가능하며, **초기화** 버튼으로 주문을 리셋하거나 **주문 확인** 버튼으로 주문 내역을 확인할 수 있습니다.

---

## 🔍 코드 상세 설명

### 1️⃣ 첫 번째 부분: 변수 선언 및 DOM 요소 선택

```javascript
let count1 = 0;
let count2 = 0;
let count3 = 0;

const firstOrderBtn = document.getElementById(`orderBtn1`);
const secondOrderBtn = document.getElementById(`orderBtn2`);
const thirdOrderBtn = document.getElementById(`orderBtn3`);

const firstQuantity = document.getElementById(`quantity1`);
const secondQuantity = document.getElementById(`quantity2`);
const thirdQuantity = document.getElementById(`quantity3`);
```

* **💡 로직 설명**: 이 부분에서는 각 메뉴(아메리카노, 라떼, 케이크)의 주문 수량을 저장하는 변수(`count1`, `count2`, `count3`)를 초기화하고, HTML에서 주문 버튼과 수량 표시 요소를 JavaScript로 가져옵니다. 이를 통해 버튼 클릭이나 수량 표시를 조작할 준비를 합니다.
* **📘 문법 설명**:
  * **`let`**: 변수 선언 키워드로, 재할당이 가능한 변수를 정의합니다. 여기서는 주문 수량을 추적하기 위해 사용됩니다.
  * **`const`**: 재할당이 불가능한 상수를 선언합니다. DOM 요소는 한 번 선택된 후 변경되지 않으므로 `const`를 사용합니다.
  * **`document.getElementById`**: HTML에서 특정 `id`를 가진 요소를 찾아 JavaScript로 조작할 수 있게 합니다. 예: `orderBtn1`은 아메리카노 주문 버튼을 가리킵니다.

### 2️⃣ 두 번째 부분: 주문 처리 공통 함수

```javascript
function handleOrder(orderButton, count, quantityDisplay) {
    count += 1;
    quantityDisplay.innerHTML = count;
    updateTotal();
    if (count === 5) {
        orderButton.disabled = true;
    }
    return count;
}
```

* **💡 로직 설명**: `handleOrder` 함수는 모든 메뉴의 주문 처리를 공통적으로 처리합니다. 주문 버튼이 클릭되면 수량을 1 증가시키고, 화면에 업데이트된 수량을 표시하며, 총 금액을 계산합니다. 수량이 5에 도달하면 버튼을 비활성화하여 추가 주문을 막습니다.
* **📘 문법 설명**:
  * **`function`**: 함수를 정의하는 키워드로, 재사용 가능한 코드 블록을 만듭니다.
  * **`innerHTML`**: HTML 요소의 내용을 변경합니다. 여기서는 수량 표시 요소에 새로운 수량 값을 업데이트합니다.
  * **`disabled`**: HTML 버튼 요소의 속성으로, `true`로 설정하면 버튼이 비활성화되어 클릭할 수 없게 됩니다.
  * **`return`**: 함수의 결과를 반환합니다. 여기서는 증가된 수량을 반환하여 각 메뉴의 `count` 변수에 저장합니다.

### 3️⃣ 세 번째 부분: 각 메뉴의 주문 처리

```javascript
firstOrderBtn.addEventListener('click', function() {
    count1 = handleOrder(this, count1, firstQuantity);
});

secondOrderBtn.addEventListener('click', function() {
    count2 = handleOrder(this, count2, secondQuantity);
});

thirdOrderBtn.addEventListener('click', function() {
    count3 = handleOrder(this, count3, thirdQuantity);
});
```

* **💡 로직 설명**: 각 메뉴의 주문 버튼(`orderBtn1`, `orderBtn2`, `orderBtn3`)에 클릭 이벤트 리스너를 추가합니다. 버튼이 클릭되면 `handleOrder` 함수를 호출하여 해당 메뉴의 수량을 증가시키고, 화면을 업데이트합니다.
* **📘 문법 설명**:
  * **`addEventListener`**: HTML 요소에 이벤트를 연결합니다. 여기서는 `click` 이벤트를 감지해 함수를 실행합니다.
  * **`this`**: 이벤트 핸들러 내에서 클릭된 요소(여기서는 버튼)를 가리킵니다. 이를 `handleOrder` 함수에 전달해 버튼을 비활성화할 때 사용합니다.

### 4️⃣ 네 번째 부분: 총 금액 계산

```javascript
function updateTotal() {
    let total = (count1 * 3000) + (count2 * 4000) + (count3 * 5000);
    document.getElementById(`totalAmount`).innerHTML = total;
}
```

* **💡 로직 설명**: `updateTotal` 함수는 각 메뉴의 수량과 가격(아메리카노 3,000원, 라떼 4,000원, 케이크 5,000원)을 곱해 총 금액을 계산하고, 이를 화면에 표시합니다.
* **📘 문법 설명**:
  * **산술 연산자 (`*`, `+`)**: 수량과 가격을 곱하고, 각 메뉴의 금액을 더해 총액을 계산합니다.
  * **`innerHTML`**: 총 금액을 표시하는 HTML 요소의 내용을 업데이트합니다.

### 5️⃣ 다섯 번째 부분: 주문 초기화

```javascript
document.getElementById(`resetBtn`).addEventListener(`click`, function () {
    count1 = 0;
    count2 = 0;
    count3 = 0;
    firstQuantity.innerHTML = 0;
    secondQuantity.innerHTML = 0;
    thirdQuantity.innerHTML = 0;
    firstOrderBtn.disabled = false;
    secondOrderBtn.disabled = false;
    thirdOrderBtn.disabled = false;
    updateTotal();
});
```

* **💡 로직 설명**: **초기화** 버튼을 클릭하면 모든 메뉴의 주문 수량을 0으로 리셋하고, 화면에 표시된 수량을 0으로 변경하며, 비활성화된 버튼을 다시 활성화합니다. 마지막으로 총 금액을 업데이트합니다.
* **📘 문법 설명**:
  * **`addEventListener`**: 초기화 버튼에 클릭 이벤트를 연결합니다.
  * **`disabled = false`**: 비활성화된 버튼을 다시 활성화합니다.
  * **`innerHTML`**: 수량 표시를 0으로 초기화합니다.

### 6️⃣ 여섯 번째 부분: 주문 확인

```javascript
document.getElementById(`confirmBtn`).addEventListener(`click`, function () {
    let orderText = `주문내역\n`;
    let total = 0;

    if (count1 > 0) {
        orderText += `아메리카노 ${count1}개 = ${count1 * 3000}원\n`;
        total += count1 * 3000;
    }

    if (count2 > 0) {
        orderText += `카페라떼 ${count2}개 = ${count2 * 4000}원\n`;
        total += count2 * 4000;
    }

    if (count3 > 0) {
        orderText += `케이크 ${count3}개 = ${count3 * 5000}원\n`;
        total += count3 * 5000;
    }

    orderText += `\n총 금액 : ${total}원`;
    alert(orderText);
});
```

* **💡 로직 설명**: **주문 확인** 버튼을 클릭하면 주문 내역을 요약한 문자열을 생성하고, `alert` 창을 통해 사용자에게 보여줍니다. 주문 수량이 0보다 큰 메뉴만 포함되며, 총 금액을 다시 계산해 표시합니다.
* **📘 문법 설명**:
  * **`if`**: 조건에 따라 코드를 실행합니다. 여기서는 수량이 0보다 큰 경우에만 주문 내역에 추가합니다.
  * **템플릿 리터럴 (`${}`)**: 문자열 내에 변수 값을 삽입할 때 사용합니다. 예: `${count1}`은 `count1`의 값을 문자열에 포함시킵니다.
  * **`alert`**: 브라우저에 팝업 창을 띄워 사용자에게 메시지를 보여줍니다.
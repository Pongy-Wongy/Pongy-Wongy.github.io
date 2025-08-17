---
layout: single
title: "JavaScript로 간단한 사칙연산 계산기 구현하기"
excerpt: "이 코드는 HTML과 JavaScript를 사용해 두 숫자와 연산자를 입력받아 사칙연산(덧셈, 뺄셈, 곱셈, 나눗셈)을 수행하는 간단한 계산기를 구현합니다. 사용자가 입력한 값을 실시간으로 계산해 결과를 화면에 표시합니다."
categories: [HTML, CSS, JavaScript]
tag: [calculator, HTML, CSS, JavaScript]
toc: true
published: true
---

# JavaScript로 간단한 사칙연산 계산기 구현하기

이 코드는 HTML로 입력 폼과 연산자 선택 드롭다운을 만들고, JavaScript로 사용자가 입력한 두 숫자와 연산자를 받아 사칙연산 결과를 표시합니다.

---

## 💻 전체 코드

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <input type="number" id="num1" placeholder="첫 번째 숫자" />
    <select id="operator">
        <option value="+">➕</option>
        <option value="-">➖</option>
        <option value="*">✖️</option>
        <option value="/">➗</option>
    </select>
    <input type="number" id="num2" placeholder="두 번째 숫자" />
    <button onclick="calculate()">계산하기</button>
    <h3>결과: <span id="result">없음</span></h3>
    <script>
        // 1. 테스트 함수
        function test() {
            return 123;
        }
        let v = test();
        console.log(v);

        // 2. 사칙연산 처리 함수
        function result(v1, v2, op) {
            if (op == "+") {
                return v1 + v2;
            } else if (op == "-") {
                return v1 - v2;
            } else if (op == "*") {
                return v1 * v2;
            } else {
                return v1 / v2;
            }
        }
        
        // 3. 계산 실행 함수
        function calculate() {
            let v1 = Number(document.getElementById("num1").value);
            let v2 = Number(document.getElementById("num2").value);
            let operator = document.getElementById("operator").value;
            console.log(v1);
            console.log(v2);
            console.log(operator);
            let resultValue = result(v1, v2, operator);
            document.getElementById(`result`).innerHTML = resultValue;
        }
    </script>
</body>
</html>
```

---

## ✨ 코드 로직 요약

이 코드는 두 개의 숫자와 연산자를 입력받아 **result** 함수로 사칙연산을 수행하고, **calculate** 함수로 입력값을 처리해 결과를 화면에 표시합니다. **test** 함수는 디버깅용으로 간단한 값을 반환하며, **onclick** 이벤트로 계산 버튼을 클릭하면 계산이 실행됩니다.

---

## 🔍 코드 상세 설명

### 1️⃣ 첫 번째 부분: HTML 구조

```html
<input type="number" id="num1" placeholder="첫 번째 숫자" />
<select id="operator">
    <option value="+">➕</option>
    <option value="-">➖</option>
    <option value="*">✖️</option>
    <option value="/">➗</option>
</select>
<input type="number" id="num2" placeholder="두 번째 숫자" />
<button onclick="calculate()">계산하기</button>
<h3>결과: <span id="result">없음</span></h3>
```

* **💡 로직 설명**: 이 부분은 사용자 입력을 받는 인터페이스를 정의합니다. 두 개의 숫자 입력 필드(`<input type="number">`), 연산자를 선택하는 드롭다운(`<select>`), 그리고 계산을 실행하는 버튼(`<button>`)이 포함됩니다. 결과는 `<span id="result">`에 표시됩니다.
* **📘 문법 설명**:
  - **input type="number"**: 숫자만 입력 가능하도록 제한합니다. `id` 속성으로 JavaScript에서 값을 가져옵니다.
  - **select**: 드롭다운 메뉴를 생성하며, 각 `<option>`의 `value` 속성은 연산자 기호(`+`, `-`, `*`, `/`)를 나타냅니다.
  - **onclick**: 버튼 클릭 시 **calculate** 함수를 호출합니다.
  - **span**: 계산 결과를 동적으로 표시하기 위한 요소로, 초기값은 "없음"입니다.

### 2️⃣ 두 번째 부분: 테스트 함수

```javascript
function test() {
    return 123;
}
let v = test();
console.log(v);
```

* **💡 로직 설명**: **test** 함수는 단순히 123을 반환하며, 디버깅이나 테스트 목적으로 사용됩니다. 반환값은 변수 `v`에 저장되고 콘솔에 출력됩니다.
* **📘 문법 설명**:
  - **function**: 함수를 정의합니다. 여기서는 **test**라는 이름의 함수를 선언합니다.
  - **return**: 함수의 실행 결과를 반환합니다. 여기서는 숫자 123을 반환합니다.
  - **console.log**: 콘솔에 값을 출력해 디버깅에 사용됩니다. 초보자는 이를 통해 코드 실행 결과를 확인할 수 있습니다.

### 3️⃣ 세 번째 부분: 사칙연산 및 계산 처리

```javascript
function result(v1, v2, op) {
    if (op == "+") {
        return v1 + v2;
    } else if (op == "-") {
        return v1 - v2;
    } else if (op == "*") {
        return v1 * v2;
    } else {
        return v1 / v2;
    }
}

function calculate() {
    let v1 = Number(document.getElementById("num1").value);
    let v2 = Number(document.getElementById("num2").value);
    let operator = document.getElementById("operator").value;
    console.log(v1);
    console.log(v2);
    console.log(operator);
    let resultValue = result(v1, v2, operator);
    document.getElementById(`result`).innerHTML = resultValue;
}
```

* **💡 로직 설명**: **result** 함수는 두 숫자(`v1`, `v2`)와 연산자(`op`)를 받아 사칙연산을 수행합니다. **calculate** 함수는 입력 필드에서 값을 가져와 **Number**로 변환한 뒤, **result** 함수를 호출해 계산 결과를 `<span id="result">`에 표시합니다.
* **📘 문법 설명**:
  - **if/else if/else**: 조건문으로 연산자에 따라 적절한 연산을 수행합니다. `==`는 값 비교를 의미합니다.
  - **Number**: 입력값(`.value`)은 문자열이므로 **Number**로 숫자로 변환합니다.
  - **document.getElementById**: HTML 요소를 ID로 선택해 값을 가져오거나 수정합니다.
  - **innerHTML**: `<span>` 요소의 내용을 동적으로 변경해 계산 결과를 표시합니다.
  - **console.log**: 입력값과 연산자를 콘솔에 출력해 디버깅을 돕습니다.

---


```
---
layout: single
title: "관계연산자"
date: 2025-06-17
categories: [블로그, 마크다운]
tags: [GitHub, Markdown, Jekyll]
---


## 관계연산자
```java

package chapter02;

public class Operator09 {

	public static void main(String[] args) {
		
		
		//관계연산자
		int num1 = 5;
		int num2 = 3;
		
		//num1이 크다고 명시
		System.out.println("num1 > num2 :" + (num1 > num2));
		//num1이 크거나 같다고 명시
		System.out.println("num1 > num2 :" + (num1 >= num2));
		//num2가 더 크다고 명시
		System.out.println("num1 < num2 :" + (num1 < num2));
		System.out.println("num1 <= num2 :" + (num1 <= num2));
		
		//num1과 num2 같냐고 명시
		System.out.println("num1==num2 :" + (num1 == num2));
		//num1과 num2가 같지 않냐고 명시
		System.out.println("num1 !=num2 :" + (num1 != num2));
	}
}

```
### 출력된 값
```java
num1 > num2 :true
num1 > num2 :true
num1 < num2 :false
num1 <= num2 :false
num1==num2 :false
num1 !=num2 :true

```
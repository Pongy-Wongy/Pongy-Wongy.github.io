---
layout: single
title: "복합대입연산자"
excerpt: "복합대입연산자 복습"
date: 2025-06-19
categories: [블로그, 마크다운]
tags: [GitHub, Markdown, Jekyll]
last_modified_at: 2025-06-19T08:06:00-05:00
---

## 복합대입연산자
```java
public class Example01 {

	
	public static void main(String[] args) {
		
		//대입연산자
		int num = 20;
		
		System.out.println("num = num + 10 : " + (num += 10));
        //변수 num에 10을 더한값 >>> 20 + 10 = 30
		System.out.println("num = num - 10 :" + (num -= 10));
        //변수 num에 10을 뺸 값 >>> 20 - 10 = 10
		System.out.println("num = num * 10 :" + (num *= 10));
        //변수 num에 10을 곱한 값 >>> 20 * 10 = 200
		System.out.println("num = num / 10 :" + (num /= 10));
        //변수 num에 10을 나눈 값 20/2 = 2
		System.out.println("num = num % 4 :" + (num %= 4));
		//변수 num에 4로 나눴을때의 나머지값 0
	}
}

```
### 출력된 값
```java
	num = num + 10 : 30
	num = num - 10 :20
	num = num * 10 :200
	num = num / 10 :2
	num = num % 4 :0
```
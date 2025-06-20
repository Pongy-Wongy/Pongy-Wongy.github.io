---
layout: single
title: "중첩for문"
excerpt: "중첩for문 복습"
date: 2025-06-20
categories: [블로그, 마크다운]
tags: [GitHub, Markdown, Jekyll]
last_modified_at: 2025-06-20T08:06:00-05:00
---

```java
package chapter03;

public class For06 {
	public static void main(String[] args) {
		
		//중첩반복문
		for (int i = 0; i < 2; i++) {
			System.out.println("외부 for문:" + i);
			
			for(int j = 0; j < 3; j++) {
				System.out.println(i + "내부 for:" + j );
			}//내부 for문
		}//외부 for문
	}//main
}

```

```java
package chapter03;

public class For07 {
	public static void main(String[] args) {
		
		for (int i= 2; i <= 9; i++) {
			System.out.println("=="+ i + "==");
			for(int j = 1; j <=9; j++) {
				System.out.println(i + "x" + j + "==" + (i*j));
			}
		}
	}

}

```
---
layout: single
title: "중첩for문"
excerpt: "중첩for문 복습"
categories: Java
tags: Java
toc: true
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
```markdown
외부 for문:0
0내부 for:0
0내부 for:1
0내부 for:2
외부 for문:1
1내부 for:0
1내부 for:1
1내부 for:2
```

```java
package chapter03;

public class For07 {
	public static void main(String[] args) {
		
		for (int i= 2; i <= 9; i++) {
			System.out.println("=="+ i + "단==");
			for(int j = 1; j <=9; j++) {
				System.out.println(i + "x" + j + "==" + (i*j));
			}
		}
	}

}

```

```java
package chapter03;

public class For08 {
	public static void main(String[] args) {
		
		int height = 5;
		for(int i=1; i <= height; i++) {
			for(int j=1; j<=i; j++) {
				System.out.print("*");
			}//내부 for문
			System.out.println();
		}//외부for문
	}

}
```
```markdown
*
**
***
****
*****
```


```java
package chapter03;

public class Example06 {
	
	public static void main(String[] args) {
		
		int height = 3;//피라미드 높이
		
		for(int i=0; i<3; i++) {
			
			//1.공백
			for(int j=0; j<height -i -1; j++) {
				System.out.println(" ");
			}
			//2. 별 출력
			for(int k=0; k<(2*i+1); k++) {
				
			}
			
		}
	}

 }
```
---
layout: single
title: "전위●후위 연산"
excerpt: "전위●후위 연산 복습"
categories: Java
tag: Java
toc: true
---


## 전위연산과 후위연산
```java
public class Example03 {
	
	public static void main(String[] args) {
		
		//전위연산
		System.out.println("==전위연산==");
		int gameScore = 150;
		int result = ++gameScore;//대입 전 연산
		System.out.println("gameScore :" + gameScore);
		System.out.println("result :" + result);
		
		System.out.println("==후위연산==");
		int gameScore2 = 150;
		int result2 = gameScore2++;//대입후 연산
		System.out.println("gameScore2 :" + gameScore2);
		System.out.println("result2 :" + result2);	
		
		System.out.println();
		
	}
}
```
### 출력된 값
```java
==전위연산==
gameScore :151
result :151
==후위연산==
gameScore2 :151
result2 :150
```
***
```java
package chapter02;

public class Example04{
	public static void  main(String[] args) {
		
		int a, b;
		a = 10;
		b = 20;
		
		System.out.println("++a : " + (++a));
		System.out.println("a++ : " + (a++));
		System.out.println("후위연산 이후 a 의 값 : " + (a++));
		
		System.out.println("--b : " + (--b));
		System.out.println("b-- : " + (b--));
		System.out.println("후위연산 이후 b의 증감(감소)값 : " + (b--));
	}
}

```
### 출력된 값
```java
++a : 11
a++ : 11
후위연산 이후 a 의 값 : 12
--b : 19
b-- : 19
후위연산 이후 b의 증감(감소)값 : 18
```
***
```java

package chapter02;

public class Example05 {
	public static void main(String[] args) {
		
		
		int x = 10;
		int y = 10;
		int z;
		
		x++;// x +=1
		++x;// x +=1
		System.out.println("x :" + x);
		
		System.out.println("---------------");//
		
		y--;// y -= 1
		--y;// y -= 1
		System.out.println("y:" + y);
		
		System.out.println("---------------");
		z = x++;
		System.out.println("x :" + x);
		System.out.println("z:" + z);
		
		System.out.println("---------------");
		z = ++x;
		System.out.println("x:" + x);
		System.out.println("z:" + z);
		
		System.out.println("---------------");
		z = ++x + y++;
		System.out.println("z :" + z);
		//
	}
}

```
### 출력된 값
```java
x :12
---------------
y:8
---------------
x :13
z:12
---------------
x:14
z:14
---------------
z :23
```


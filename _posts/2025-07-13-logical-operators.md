---
layout: single
title: "논리연산자"
excerpt: "논리연산자 복습"
categories: Java
tag: Java
toc: true
---

## 논리연산자

```java

package chapter02;

public class Operator11 {
	public static void main(String[] args) {
		//논리연산자
		
		// || (논리합) : 두 조건 중 어느 한 조건이라도 참이면 결과는 참
		System.out.println("OR연산 (두 조건이 모두 참):" + (true || true));//true
		System.out.println("OR연산 (두 조건 중 하나가 참):" + (true || false));//true
		System.out.println("OR연산 (두 조건이 모두 거짓):" + (false || false));//false
		
		//&& (논리곱, and연산 : 두 조건이 모두 참이어야 결과가 참
		System.out.println("AND연산 (두 조건이 모두 참):" + (true && true));//true
		System.out.println("AND연산 (두 조건중 하나만 참):" + (true && false));//false
		System.out.println("AND연산 (두 조건이 모두 거짓):" + (false && false));//false
	}
}
```

### 출력된 값
```java
OR연산 (두 조건이 모두 참):true
OR연산 (두 조건 중 하나가 참):true
OR연산 (두 조건이 모두 거짓):false
AND연산 (두 조건이 모두 참):true
AND연산 (두 조건중 하나만 참):false
AND연산 (두 조건이 모두 거짓):false
논리부정연산(참을 거짓으로):false
논리부정연산(거짓을 참으로):true
```

```java
package chapter02;

public class Operator12 {

	public static void main(String[] args) {
		
		//논리연산자
		int num1 = 10;
		int num2 = 20;
		
		System.out.println("---AND---");
		boolean flag1 = (num1 > 10) && (num2 > 20);
		System.out.println("false && false:" + flag1);
		
		boolean flag2 = (num1 > 10) && (num2>=20);
		System.out.println("false && tree :" +flag2);
		
		boolean flag3 = (num1 > 0) && (num2 == 20);
		System.out.println("true && true :" + flag3);
		
		System.out.println("-----OR------");
		
		boolean flag4 = (num1 > 10) || (num2 > 20);
		System.out.println("false || false :" + flag4);
		boolean flag5 = (num1 >= 10) || (num2 > 20);
		System.out.println("tree || false :" + flag5);
		boolean flag6 = (num1 >= 10) || (num2 >= 20);
		System.out.println("true || true :" + flag6);
		
		System.out.println("----NOT----");
		boolean flag7 = !(num1 != num2); // !true = false
		System.out.println(flag7);
 	}
}
```

### 출력된 값
```java
---AND---
false && false:false
false && ture :false
true && true :true
-----OR------
false || false :false
true || false :true
true || true :true
----NOT----
false
```
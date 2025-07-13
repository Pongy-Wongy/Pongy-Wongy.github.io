---
layout: single
title: "Switch-case"
excerpt: "Switch-case 복습"
categories: Java
tags: Java
toc: true
---

```java
public class SwitchCase01 {
	
	public static void main(String[] args) {
		
		//조건문 - switch case문
		
		int ranking = 1;
		String medal = "";
		
		switch (ranking) {
		case 1:
			medal = "금메달";
			break;
		case 2:
			medal = "은메달";
			break;
		case 3:
			medal = "동메달";
			break;
			
		default:
			medal = "노메달";
			break;
		}
		
		System.out.println("메달의 색 :"+ medal);
	}
}
```

```java

package chapter03;

import java.util.Scanner;

public class SwitchCase02 {
	
	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		
		System.out.println("번호를 선택하세요");
		System.out.print("1.조회 | 2.출금 | 3. 입금 >>>>");
		int num = Integer.parseInt(scan.nextLine());
		
		switch (num) {
		case 1:
			System.out.println("예금조회를 선택하셨씁니다.");
			break;
		case 2:
			System.out.println("출금을 선택하셨씁니다.");
			break;
		case 3:
			System.out.println("입금을 선택하셨씁니다.");
			
		default:
			System.out.println("잘못된 번호를 입력하셨습니다.");
			break;
		}
	}

}
```
실행
```markdown
번호를 선택하세요
1.조회 | 2.출금 | 3. 입금 >>>>
```
```markdown
1번선택
번호를 선택하세요
1.조회 | 2.출금 | 3. 입금 >>>>1
예금조회를 선택하셨씁니다.
```


```java

public class SwitchCase03 {
	
	public static void main(String[] args) {
		
		int month = 2;
		int day;
		
		switch (month) {
		case 1: case 3: case 5: case 7: case 8: case 10:
			day = 31;
			break;
		case 2: 
			day =28;
			break;
		case 4: case 6: case 9: case 11:
			day = 30;
			break;
		default:
			day = 0;
			break;
		}
		
		System.out.println(month + "월은" + day + "일까지 있습니다." );
	}

}
```

```java
public class SwitchCase03 {
	
	public static void main(String[] args) {
		
		int month = 2;
		int day;
		
		switch (month) {
		case 1: case 3: case 5: case 7: case 8: case 10:
			day = 31;
			break;
		case 2: 
			day =28;
			break;
		case 4: case 6: case 9: case 11:
			day = 30;
			break;
		default:
			day = 0;
			break;
		}
		
		System.out.println(month + "월은" + day + "일까지 있습니다." );
	}

}


```java
public class SwitchCase03 {
	
	public static void main(String[] args) {
		
		int month = 2
				;
		int day;
		
		switch (month) {
		case 1: case 3: case 5: case 7: case 8: case 10:
			day = 31;
			break;
		case 2: 
			day =28;
			break;
		case 4: case 6: case 9: case 11:
			day = 30;
			break;
		default:
			day = 0;
			break;
		}
		
		System.out.println(month + "월은" + day + "일까지 있습니다." );
	}

}

```markdwon
2월은28일까지 있습니다.
```

```java
public class Example03 {
	
	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		System.out.println("등급을 입력하세요(A, B, C) : ");
		String grade = scan.nextLine();
		
		//A -> 우수고객, B -> 일반회원 그 외 ->
		
		switch (grade) {
		case "A":
			System.out.println("우수고객"); 
			break;
		case "B":
			System.out.println("일반회원"); 
			break;
		
		default:
			break;
		}
		
		}
	}
```

```markdwon
등급을 입력하세요(A, B, C) : 
B
일반회원
```
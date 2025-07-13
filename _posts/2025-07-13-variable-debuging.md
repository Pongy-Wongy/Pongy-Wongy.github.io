---
layout: single
title: "지역변수"
excerpt: "지역변수 복습"
categories: Java
tag: Java
toc: true
---

```java
package chapter03;

public class Scorp01 {
	 public static void main(String[] args) {

	        //지역변수
	        int x = 10;

	        if(true) {
	            int y = 20;
	            System.out.println("x :" + x);
	            System.out.println("y :" + y);
	        }
	        System.out.println("x :" + x);
	        System.out.println("y :" + y);
	    }
	    int y = 30;
}
```

```java
package chapter03;

public class Scorp02   {
    public static void main(String[] args) {

        for(int i = 0; i<5; i++) {
            System.out.println("내부 인덱스 i :" + i);
            String str = "반복문 내 지역변수";
            System.out.println(str);
            int count = 0;
            System.out.println("반복문 내에서 선언한 변수:" + count);
            count++;
            System.out.println("증가한 값" + count);
            System.out.println("==================");

        }
    }
}
```


```java
    package chapter03;

    public class Scorp03 {

        public static void main(String[] args) {

            int i;
            String str  ="반복문 외부 지역변수";

            for(i = 0; i<5; i++) {
                System.out.println("인덱스 i:" + i);
                System.out.println(str);
                System.out.println("==========");
            }
                System.out.println("인덱스 i:" + i);
                System.out.println(str);
        }
    }
```

```java
package chapter03;

public class Scorp4 {
	public static void main(String[] args) {
		
		int num = 2
				
		switch (key) {
		case 1:{
			String select = "1번 선택됨(switch내부 변수)"
			System.out.println(select);
			break;
		}
		case 2:{
			String select = "1번 선택됨(switch내부 변수)"
			System.out.println(select);
			break;
		}
		default:
			break;
		}
		//System.out.println(select);//select는 switch-case 블록 안에서만 유효
	}
}
```
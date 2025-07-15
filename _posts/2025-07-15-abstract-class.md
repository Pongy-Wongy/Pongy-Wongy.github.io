---
layout: single
title: "추상클라스와 인터페이스"
excerpt: "추상클라스,인터페이스 복습"
categories: Java
tag: [Java, class, interface]
toc: true
---

# 추상클라스,인터페이스 문법 개념 복습

## 추상클라스
아직 완성되지 않은 클래스
1. 메서드 선언만 있고 구현은 없는 메서드. 자시클래스에서 반드시 구현해야 한다
2. 인스턴스 불가
직접적인 객체 생성 불가. 상속을 통해서만 사용  
3. 상속을 위한 기반 클래스
다른 클래스들이 상속받아 기능을 확창 구체화할 수 있도록 설게

```markdown
abstract class 클라스명 {

}
```

```java
//추상메서드 정의
abstract class Shape{
    abstract double calculateArea();
}/

//추상클라스 구현
class Square extends Shape{
    private double s;
    public Square(double s){
        this.s=s;
    }
    double CalculateArea(){
        retrun s*s;
    }
}
```

---------------------------------------

## 인터페이스
클래스를 작성할때 기본이 되는 뼈대

```markdown
interface 인터페이스명{

}
```

```java
interface Shape{
    double calculateArea();//도형넓이메소드
}

//인터페이스 구현
class Square implements Shape{
    private double s;
    public Square(double s) {
        this.s = s;
    }
    double calculateArea(){
        return s*s;
    }
}
```


---
layout: single
title: "Class 복습"
excerpt: "Class-Java문법개념 복습"
categories: Java
tag: [Java, class]
toc: true
---

# Class 문법 개념 복습

## Class
Class:(설계도): 데이터와 기능을 포함하는 코드 묶음  
객체: 설계도에 따라 만들어진 것  
ex. 아파트 설계도(아파트 클라스)로 만들어진 아파트(객체)가 객체이다  

```java
class Person{

}

public static void main(String[] args){
    Person person = new Person();
}
```
  -------------------------------

## 인스턴스 변수
클래스 내에 선언된 변수  
```java
class Person{
    String name;//인스턴스 변수
    int age;//인스턴스 변수
}

public static void main(String[] args){
    Person person = new Person();
    person.name = "철수";
    person.age = 20;
}
```
1. 점(.)으로 인스턴스 변수에 접근  
2. 인스턴스 변수? 객체마다 서로 다른 값을 가질 수 있다.  
  
  -------------------------------

## 클래스 변수
클래스 내에 static으로 선언된 변수
```markdown
class 클래스명 {
    static 클래스 변수1
    static 클래스 변수2
}
```

```java
class Person{
    String name;//인스턴스 변수
    int age;//인스턴스 변수
    static int personCount = 0; //클래스 변수
}
```

메인메소드 호출
```java
public static void main(String[] args){
   Person.personCount = 10
   System.out.println(PePerson.personCount) //10출력
}
```

1. 클래스 변수? 객체를 만들 필요없이 클래스 명으로 접근

-------------------------------

## 인스턴스 메소드
클래스 내에 정의된 메소드
```java
class Person{
    String name;//인스턴스 변수
    int age;//인스턴스 변수
    static int personCount = 0; //클래스 변수
    
    //인스턴스 메소드
    public void introduce() {
        System.out.println("이름: " + name);
        System.out.println("나이: " + age);
    }
}
```

메인메소드 호출
```java
public static void main(String[] args){
Person person = new Person();//객체생성
person.name = "철수";
person.age = 20;
person.intrduce();
}
/*출력
이름: 철수
나이 : 20
*/
```
1. 점(.)으로 인스턴스 변수 or 메소드에 접근

-------------------------------

## 클래스 메소드  
클래스 내에 static 으로 정의된 메소드
```markdown
class 클래스명 {
    static 클래스 메소드1
    static 클래스 메소드2
}
```

```java
    class Person{
    String name;//인스턴스 변수
    int age;//인스턴스 변수
    static int personCount = 0; //클래스 변수

    //클래스 메소드
    public static void printPersonCount(){
        System.out.println(personCount)
    }
    }
```

메인호출
```java
public static void main(String[] args){
    Person.personcount=10;
    Person.printPersonCount();
}
```
-------------------------------

## This?
자기 자신(인스턴스/지역변수 구분)
```markdown
this.인스턴스 변수;
```
 
```java
class Person{
    String name;
    public void setNam(String name) {
        this.name = name;
        //this.name >>> 인스턴스 변수
        
    }
}
```

메인호출
```java
Person person = new Person
person.setName("철수");
System.out.println(person.name);// 출력 >>> 철수
```
-------------------------------

## 생성자
객체가 생성될떄 호출되는 메소드
```markdown
클래스명(전달값){
    초기화 명령문
}
```

```java
class Person{
    String name;
    int age;
    Person(String name. int age){
        this.name = name;//초기화 작업
        this.age = age;//초기화 작업
    }
}
```

메인호출
```java
public static void main(String[] args) {
    Person person = new Person("철수", 20);
}
```

-------------------------------------------

## Getter 와 Setter
Getter : 인스턴스 변수의 값 반환(가져오기)
Setter : 인스턴스 변수의 값 설정
```markdown
Getter
반환형 get이름(){
    return 반환값;
}

Setter
void set이름(전달값){

}
```

```java
//Getter
class Person {
    int age;
    public int getAge() {
        return age;
    }
}

//Setter
class Person {
    int age;
    public void setAge(int age) {
        this.age = age;
    }
}

//Getter&Setter
public static void main(String[] args){
    Person person = new Person();
    person.setAge(20);//값 설정하기(setter)
    System.out.println(person.getAge());//값 가져오기
}
```

-------------------------------------------------

## 접근 제어자
접근 권한 지정
```markdown
clss 클래스명 {
    인스턴스 변수
    인스턴스 메소드
}

private : 해당 클래스 내에서만
public : 모든 클래스에서
default : 같은 패키지 네에서만(아무것도 적지 않을떄)
protected : 같은 패키지 내에서, 다른 패키지인 경우 자식 클래스에서
```
---------------------------------------------------

## 상속
특정 클래스의 기능을 재사용 및 확장

```markdown
부모클래스: 기능1, 기능2 
>>>>>>>>>>>>>>>>>>>>>자식 클래스: 기능1,기능2 + 기능3(추가)(부모클래스의 기능 재사용(기능1,기능2))

class 자식클래스명 extends 부모 클래스명{

}
```

```java
class Student extends Person {
    String School;
}
```

----------------------------------------------------------

## 메소드 오버라이딩
부모 클래스의 메소드 재정의
```java
//부모클래스
class Persion{
    public void introduce() {
        System.out.println("사람입니다")
    }
}

//자식클래스
class Student extends Person{
    public void introduce(){
        System.out.println("학생입니다")
    }
}
```

----------------------------------------------------------

## 다형성
여러 형태로 동작할 수 있는 성질

### 다형성의 중요성
1. 유연한 코드 작성
- 다양한 객체를 하나의 타입으로 관리 가능

2. 코드 재사용성과 확장성 향상
- 유지보수가 쉬어지고, 새로운 클라스 추가가 용이함
```java
class Person{
    public void introduce(){
        System.out.println("사람입니다")
    }
}
class Student extends Person{
    public void introduce(){
        System.out.println("학생입니다")
    }
}

///메인호출
public static void main(String[] args){
    Person person = new Person();

    Person student = new Student();//중요
    //Person 타입의 변수지만,실제 객체는 Student (업캐스팅)


    person.introduce();
    student.introduce();
}
```
```html
<table>
  <thead>
    <tr>
      <th>구분</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>컴파일 시점</td>
      <td>student는 Person 타입으로 판단 → Person 클래스에 introduce()가 있는지만 확인함</td>
    </tr>
    <tr>
      <td>실행 시점</td>
      <td>student 안에 실제 객체가 Student이므로 → Student의 introduce() 호출됨</td>
    </tr>
  </tbody>
</table>
```












---
layout: single
title: "컬렉션"
excerpt: "여러가지 컬렉션에 대해 복습"
categories: Java, Collection
tag: [Java, Collection]
toc: true
---

# 컬렉션 복습
1. 제네릭스
4. ArrayList
5. LinkedList
7. HashSet
8. HashMap
9. Iterator

## 제네릭스
다양한 형태의 데이터를 다룰 수 있게한다. 
```java
package collection01;

class PrintGeneric <T>{
	T value;

	public T getValue() {
		return value;
	}

	public void setValue(T value) {
		this.value = value;
	}
}

public class Generic01 {
	
	public static void main(String[] args) {
		
		PrintGeneric<Integer> print01 = new PrintGeneric<Integer>();
		//객체 생성 시점에서 타입을 지정
		print01.setValue(10);
		Integer value01 = print01.getValue();
		System.out.println(value01);//>>>>출력: 10
		
		PrintGeneric<String> print02 = new PrintGeneric<String>();
		print02.setValue("안녕하세요");
		String value02 = print02.getValue();
		System.out.println(value02);//>>>> 출력: 안녕하세요
	}
}
```

-----------------------------------------------------

## ArrayList
배열기반 리스트, 빠른접근 + 순차저장
ArrayList<T> 
T 는 데이터타입

```java
public static void main(String[] args){
    ArrayList<String> list = new ArrayList<>();
    list.add("철수");
    list.add("영희")

    for(String s : list){
        System.out.println(s)// 출력 : 철수,영희
    }
}
```
<table>
        <caption>ArrayList</caption>
        <thead>
            <tr>
                <th>기능</th>
                <th>설명</th>
                <th>예시</th>
                <th>결과</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>add</td>
                <td>추가</td>
                <td>list.add("철수");</td>
                <td>{"철수"}</td>
            </tr>
            <tr>
                <td>get</td>
                <td>가져오기</td>
                <td>list.get(0);</td>
                <td>"철수"</td>
            </tr>
            <tr>
                <td>size</td>
                <td>크기</td>
                <td>list.size();</td>
                <td>1</td>
            </tr>
            <tr>
                <td>set</td>
                <td>수정</td>
                <td>list.set(0, "영희");</td>
                <td>{"영희"}</td>
            </tr>
            <tr>
                <td>contains</td>
                <td>포함 여부</td>
                <td>list.contains("영희");</td>
                <td>true</td>
            </tr>
            <tr>
                <td>remove</td>
                <td>삭제</td>
                <td>list.remove("영희");</td>
                <td>{}</td>
            </tr>
            <tr>
                <td>clear</td>
                <td>전체 삭제</td>
                <td>list.clear();</td>
                <td>{}</td>
            </tr>
        </tbody>
    </table>

### List로 멤버정보 출력하기

```java
멤버클래스
class Member {
	
	String name;
	int age;

    public Member(String name, int age) {
        this.name = name;
        this.age = age;
    }
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
	@Override
	public String toString() {
		return "Member [name=" + name + ", age=" + age + "]";
	}
	
}
```
```java
package chapter15.list;

import java.util.ArrayList;
import java.util.List;

public class ArrayList03 {

	public static void main(String[] args) {
		
		List<Member> memberList = new ArrayList<Member>();
		memberList.add(new Member("홍길동", 15));
		memberList.add(new Member("이순신", 25));
		memberList.add(new Member("장보고", 18));
		memberList.add(new Member("이순신", 25));
		memberList.add(new Member("강감찬", 45));
		
		for(Member m : memberList) {
			System.out.println(m);
		}
		
	}
}

```
출력 값
```markdown
Member [name=홍길동, age=15]
Member [name=이순신, age=25]
Member [name=장보고, age=18]
Member [name=이순신, age=25]
Member [name=안중근, age=45]
```

## LinkedList







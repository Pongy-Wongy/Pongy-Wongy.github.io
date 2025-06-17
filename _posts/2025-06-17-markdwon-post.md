---
layout: single
title: "Markdwon 문법 배우기"
date: 2025-06-17
categories: [블로그, 마크다운]
tags: [GitHub, Markdown, Jekyll]
---

## 1. markdwon 특징
markdown은 텍스트 기반의 마크업 언어이다. 문법이 간단한 것이 특징이다. 간단한만큼 가독성이 좋고 배우기가 쉽다. GitHub를 많이 사용해보았다면 README 파일이 모두 markdown으로 작성되었음을 보았을 것이다. GiuHub가 markdown을 사용하면서 markdown이 널리 쓰이는 계기가 되었다.

텍스트(Text)로 기반으로 작성되기 때문에 특별한 형태의 에디터가 필요가 없고 파일 사이즈가 작다. 텍스트로 이뤄져서 GitHub에서 버전관리가 용이하다.  

## 2. 마크다운 문법
기본적인 마크다운 문법을 정리하였다. markdown 문법을 먼저 표기하고 그 뒤로 html으로 표시되는 결과를 표시하였다.  

### 2.1. 텍스트 줄바꿈

```markdown
기본적인 텍스트 표기 방식이다.  
마크다운은 줄바꿈을 인식하지 않는다.

줄바꿈을 하기 위해서는 라인 끝에 스페이스를 2번  
표기해야 한다.

여러가지 강조 표시가 존재한다. 첫번째로 *single asterisks*,  
두번째로 _single underscores_, 세번째로 **double asterisks**,  
네번째로 __double underscores__, 다섯번째로 ~~cancelline~~가 있다.
```
기본적인 텍스트 표기 방식이다. 마크다운은 줄바꿈을 인식하지 않는다.

줄바꿈을 하기 위해서는 라인 끝에 스페이스를 2번
표기해야 한다.

여러가지 강조 표시가 존재한다. 첫번째로 single asterisks, 두번째로 single underscores, 세번째로 double asterisks, 네번째로 double underscores, 다섯번째로 cancelline가 있다.

  
### 2.2 글머리 달기
```markdown
# This is a H1
```
# This is a H1  

```markdOWn
## This is a H2
```
## This is a H2

```markdown
### This is a H3
```
### This is a H3 

```markdown
#### This is a H4
```
#### This is a H4 

```markdown
##### This is a H5
```
##### This is a H5 

```markdown
###### This is a H6
```
###### This is a H6  



### 2.3 인용  
인용문을 사용할때는 ">" 블럭 인용문자를 사용하면, 단계별 깊이를 지원한다.
```markdown
> This is  a bloKqute.  
```  
  
단계별 인용
```markdown
> This is a first blockqute.
>> This is a second blockqute.
>>> This is a third bloclqute.
```

> This is a first blockqute.
>> This is a second blockqute.
>>> This is a third bloclqute.



### 2.4 정렬 목록
```markdown
1. 봄
2. 여름
3. 가을
4. 겨울
```

1. 봄
2. 여름
3. 가을
4. 겨울

### 2.4 비정렬 목록
```markdown
*과자
    *라면
        *사탕
```
*과자  
    *라면  
        *사탕  

```markdown
+과자  
    +라면
        +사탕
```

+과자  
    +라면  
        +사탕

### 2.5 코드 인용(JAVA)
현재 JAVA언어를 배우고 있어 예시를 JAVA로 헸다.  

변수 4개를 선언하고 값을 대입한 후 출력하시오(10, 3.14, 'A', false)  

```java  
int iNum0 = 10;
double dNum0 = 3.14;
char a = 'A';
boolean f = false;

System.out.println(iNum0);
System.out.println(dNum0);
System.out.println(a);
System.out.println(f);
```
```java
10.0
3.14
A
false
```
  


자동 형변환 - result1이라는 double형 변수를 만들고, 변수 iNum을 double형으로 자동 형변환하세요.  

```java
int iNum = 10;
double result1 = iNum;
System.out.println(result1);
```

```java
10.0
```
double 64bit 실수형 데이터 타입중 하나이다(float보다 더 높은 정밀도를 제공)
10 이 10.0으로 바뀐걸 알 수 있다.
  
  

강제 형변환 - result2라는 int형 변수를 만들고, 변수 dNum을 int형으로 강제 형변환하세요.  
  
```java
double dNum = 20.5;
int result2 = (int)dNum;
System.out.println(result2);
```

```java
20
```

이 부분이 핵심 🔥
dNum은 double 타입이니까, 바로 int 변수에 넣을 수 없다
(왜냐면 int는 정수만 저장하고, double은 소수까지 저장하니까 손실이 날 수 있다)

그래서 int로 **강제 형변환(casting)**을 해줘야 한다.

(int)dNum 의 의미:
dNum을 int 타입으로 변환하라는 뜻.

이 형변환은 **소수점 이하를 버림(내림이 아님!)**하고, 정수 부분만 남긴다.



### 2.6 수평선
모두 수평선을 만드는 여려가지 표기법  
  
```markdown
* * *
***
***** 
- - -
-------------------------------
```



### 2.7 링크
```markdown
- 링크 표시법 : [Title](link)
[Youtube 페이지 링크](https://www.youtube.com/)
```
[Youtube 페이지 링크](https://www.youtube.com/)

● 주소 직접 표시법  
```markdown
<https://www.youtube.com>
```  
  


### 2.8 표 만들기
● 표 내용 중앙 정렬
```markdown
| 항목 | 가격 | 개수 |
|:---:|:----:|:----|
| 라면 | 800원 | 10개 |
| 과자 | 900원 | 20개 |
```
  


### 2.9 이미지 삽입
```markdown
![](https://github.com/Pongy-Wongy/Pongy-Wongy.github.io/tree/master/assets/images/coding-boy.png)
```
![](https://github.com/Pongy-Wongy/Pongy-Wongy.github.io/tree/master/assets/images/coding-boy.png)

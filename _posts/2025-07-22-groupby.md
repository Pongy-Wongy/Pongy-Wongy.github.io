---
layout: single
title: "GroupBy"
excerpt: "GroupBy이해하기"
categories: OracleSQL
tag: OracleSQL
toc: true
---

오늘은 화요일 아침이다....학원가기전 글 포스팅중이다
어제 학원을 결석했다. 왜인지 그냥 너무 가기시러서 가지않았다
근데 후회중이다. 학원을 갔으면 진작에 끝날 포스팅이었는데
단톡방에 올라온 톡을 보니 groupby에 대해서 배우는 중인것 같았다
그래서 혼자서 공부했고 이제 포스팅중이다.

## GROUPBY
**GROUP BY**는 SQL에서 SELECT문의 결과를 하나 이상의 컬럼 값을 기준으로 그룹화하여, 
각 그룹마다 **SUM, COUNT, AVG, MAX, MIN** 같은 **집계 함수**를 사용할 수 있게 합니다.

즉, 비슷한 값들을 묶어서 요약 통계를 낼 때 사용됩니다.

### 기본문법
```sql
SELECT 컬럼1, 집계함수(컬럼2)
FROM 테이블명
GROUP BY 컬럼1;
```

```sql
create table book(
    bookid number primary key, 
    bookname varchar2(40),
    publisher varchar2(40),
    price number
);
create table customer(
    custid number,
    name varchar2(20),
    address varchar2 (20),
    phone varchar2(20),
    primary key(custid)
);
create table orders(
    orderid number(10),
    orderdate number,
    custid number references customer(custid),
    bookid number references book(bookid),
    primary key(orderid)
);
```
 
 그럼 예제를 보고 문제를 풀어보자

### 예제
1. 고객별 주문 건수 구하기
```sql
select custid, count(*) as 고객별
from orders 
group by custid;
```

### 햇갈리는 오류 쿼리문
1. 별칭주의

```sql
select cs.custid, count(*) as 고객별
from orders od
group by cs.custid;
```
위에 쿼리문은 오류인데 그이유는 cs라는 별칭은 customer 테이블에 붙여야 하는데, 
이 쿼리에서는 customer 테이블이 아예 등장하지 않았기 때문에 cs.custid는 사용할 수 없습니다.

2. 컬럼과 테이블
```sql
select publisher, avg(price) as 평균
from orders od
group by publisher;
```
**orders 테이블**에는 **publisher**나 **price 컬럼**이 없습니다.
이 컬럼들은 book 테이블에 있으므로, **book 테이블**을 **JOIN**해야 합니다.

## 문제
1. 고객 이름(name)별로 몇 번 주문했는지 구하시오.
```sql
select cs.name, count(*) as 고객이름별주문횟수
from orders od
join customer cs
on cs.custid = od.custid
group by cs.name;
```

2. 책 이름(bookname)별로 몇 번 주문되었는지 구하시오.
```sql
select b.bookname, count(*) as 책이름별주문횟수
from orders od
join book b
on b.bookid = od.bookid
group by b.bookname;
```

3. 고객 주소(address)별로 주문한 고객 수를 구하시오
```sql
select cs.address, count(*) as 주소별로로주문한고객수
from orders od
join customer cs
on cs.custid = od.custid
group by cs.address;
```

4. 출판사(publisher)별로 등록된 책의 수를 구하시오.
```sql
select b.publisher, count(*) as 책의수
from orders od
join book b
on b.bookid = od.bookid
group by b.publisher;
```

5. 고객 ID(custid)별로 주문한 책의 총 가격을 구하시오.
```sql
select od.custid, sum(price) as 총가격
from orders od
join book b 
on b.bookid = od.bookid
group by od.custid;
```

6. 책 ID(bookid)별로 주문한 고객 수를 구하시오.
```sql
select bookid, count(*) as 고객수
from orders 
group by bookid;
```

7. 책 제목(bookname)별로 해당 책의 가격 합계를 구하시오.
```sql
select b.bookname, sum(price) as 총합
from orders od
join book b 
on b.bookid = od.bookid
group by b.bookname;
```


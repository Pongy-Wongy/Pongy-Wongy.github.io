---
layout: single
title: "GROUPING SETS"
excerpt: "GROUPING SETS이해하기"
categories: OracleSQL
tag: OracleSQL
toc: true
published: true
---

어제 학원을 못나와서 혼자 독학 후 group by,having,case를 포스팅했는데
포스팅이 안돼서 멘붕이었는데 마침 방금 해결해서 오늘 수업한 내용을 포스팅 할
수 있게 됨 ㅋㅎㅋㅎㅎㅋㅎㅋㅎ

## GROUPING SETS
GROUPING SETS는 GROUP BY 절에서 여러 가지 그룹화 기준을 한 번에 지정할 수 있는 고급 집계 기능입니다.
중복 계산 없이 효율적으로 다양한 집계 결과를 한 번에 조회할 수 있습니다.
기본적으로는 **GROUP BY 절에서 여러 GROUP BY 결과를 동시에 얻고 싶을 때 사용**합니다.

## 기본문법
```sql
SELECT 컬럼1, 컬럼2, 집계함수     
FROM 테이블명
GROUP BY GROUPING SETS (
    (컬럼1, 컬럼2),
    (컬럼1),
    (컬럼2),
    ()
);
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

## 예제

1. 고객별 출판사별 전체 매출 집계
```sql
select cs.name, b.publisher, sum(b.price) as 매출
from orders od
join customer cs
on cs.custid = od.custid
join book b
on b.bookid = od.bookid
group by grouping sets(
    (cs.name),
    (b.publisher)
);
```




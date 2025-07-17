---
layout: single
title: "OrcaleSQL JOIN"
excerpt: "JOIN 이해하기"
categories: OracleSQL
tag: OracleSQL
toc: true
---

오늘은 DML의 JOIN에 대해서 수업했다
JOIN은 서브쿼리문을 쓰는것보다 훨씬 간단한 것 같다.

## JOIN이란?
두 개 이상의 테이블을 **공통 컬럼(보통은 외래 키와 기본 키)**을 기준으로 연결하여 데이터를 조회하는 SQL 연산자입니다.
논리적으로 연결된 데이터를 한 번에 조회할 수 있게 해줍니다.

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
### JOIN 기본문법
```sql
SELECT 컬럼목록
FROM 테이블1
[JOIN 유형] 테이블2
ON 테이블1.컬럼 = 테이블2.컬럼;
```

### JOIN 문제
1. 한 번이라도 판매된 책의 이름과 가격을 출력
```sql
select b.bookname, b.price
from book b
join order od
on b.bookid = od.bookid;
--**공통 컬럼(기본키 = 외래키) 연결**
```

2. 20000원 이상의 도서를 주문한 고객의 이름과 주소를 조회
```sql
select cs.name, cs.address
from customer cs
join orders od
on cs.custid = od.custid
join book b
on b.bookid = od.bookid
where b.price > 20000;
```

3. 가장 가격이 저렴한 도서를 주문한 고객의 이름과 전화번호를 조회
```sql
select cs.name, cs phone
from customer cs
join orders od
on cs.custid = od.custid
join book b
on b.bookid = od.bookid
where b.price = (
    select min(price) 
    from book);
```

4. 평균 도서 가격보다 비싼 도서를 주문한 고객의 이름을 조회
```sql
select cs.name
from custoemr cs
join orders od
on cs.custid = od.custid
join book b
on b.bookid = od.bookid
where b.price > (
    select avg(price) 
    from book);

```
    
5. 2022년 1월 1일 이후에 주문한 고객의 이름을 조회
```sql
select cs.name
from customer cs
join orders od
on cs.custid = od.custid
where od.orderdate >= 
2022-01-01;
```
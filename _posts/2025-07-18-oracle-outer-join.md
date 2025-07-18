---
layout: single
title: "OrcaleSQL JOIN"
excerpt: "JOIN 이해하기"
categories: OracleSQL
tag: OracleSQL
toc: true
---

오늘은 오라클 chapter01 수업이 끝났다
오늘은 외부조인(outer join)에 대해서 배웠다.
left right 좀 많이 햇갈린다. 연습문제를 만들어서
많이 풀어봐야 되겠다.

## OUTER JOIN?

두 테이블을 연결할 때, 한쪽에만 있는 데이터도 포함해서 보여주는 조인 방식

즉, 데이터가 없어도 보여준다
→ null로라도 채워서 보여주는 조인입니다.

<table border="1">
  <thead>
    <tr>
      <th>조인 종류</th>
      <th>기준이 되는 테이블</th>
      <th>없는 데이터는 어떻게?</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>LEFT OUTER JOIN</td>
      <td>왼쪽 테이블 기준</td>
      <td>오른쪽에 없으면 null로 표시</td>
    </tr>
    <tr>
      <td>RIGHT OUTER JOIN</td>
      <td>오른쪽 테이블 기준</td>
      <td>왼쪽에 없으면 null로 표시</td>
    </tr>
    <tr>
      <td>FULL OUTER JOIN</td>
      <td>양쪽 테이블 모두 기준</td>
      <td>어느 쪽에 없든 null로 표시</td>
    </tr>
  </tbody>
</table>

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

## 외부조인 예시

책을 한 번도 사지 않은 고객도 모두 보여주는 SQL문은? (단, 고객 이름도 함께 보여준다)

```sql
select cs.custid, cs.name, od.orderid
from customer cs
left outer join orders od
on cs.custid = od.custid;
```
### LEFT JOIN
1. **왼쪽 표(customer)는 무조건 다 보여준다**
2. 오른쪽 표(orders)는 주문한 게 있을 때만 보여준다
3. 주문 안 한 고객도 나오지만, 주문 내용은 없음(null)으로 나온다
예를 들어,
철수는 주문했어요 → 철수 정보 + 주문 정보
주문 안 했어요 → 영희 정보 + 주문 정보 없음(null)

그럼 위의 코드를 **RIGHT JOIN**으로 바꿔보자

```sql
select cs.custid, cs.name, od.orderid
FROM orders od
RIGHT OUTER JOIN customer cs
ON cs.custid = od.custid;
```
### RIGHT JOIIN
1. **오른쪽 표(customer)는 무조건 다 보여준다**
2. 왼쪽 표(orders)는 주문한 게 있을 때만 보여준다
3. 주문 안 한 고객도 나오지만, 주문 내용은 없음(null)으로 나온다

## 외부조인 연습문제
1. 주문은 있었지만, 주문한 고객 정보가 없는 주문만 찾는 SQL은?  

**LEFT JOIN**
```sql
select cs.custid od.orderid
from orders od
left join customer cs
on cs.custid = od.custid
where cs.custid is null
```

**RIGHT JOIN**
```sql
select cs.custid od.orderid
from customer cs
right join orders od
on cs.csutid = od.custid
where cs.custid is null
```

이렇게 연습문제를 풀어 보았는데 하다보니깐 이해가 된다.
다음에 업데이트때는 좀더 심화된 문제를 풀어봐야겠다.




---
layout: single
title: "Having"
excerpt: "Having 이해하기"
categories: OracleSQL
tag: OracleSQL
toc: true
published: true
---

전 포스팅에서 GroupBy에 대해서 배웠다, 이번 포스팅에서는 having을 배워볼건데 
having이란 간단히 말하면 groupby와  같이 쓸 수 있는 조건절이다.

## HAVING
**HAVING**은 **GROUP BY**로 그룹화된 각 그룹에 대해 **조건**을 걸어 결과를 제한하는 데 사용됩니다.

### 기본문법
```sql
SELECT 컬럼1, 집계함수(컬럼2)
FROM 테이블명
--WHERE 조건
GROUP BY 컬럼1
HAVING 집계조건;

```

### HAVING 과 WHERE
<table border="1">
  <thead>
    <tr>
      <th>구분</th>
      <th>WHERE</th>
      <th>HAVING</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>적용 시점</td>
      <td>그룹화 <strong>이전</strong>에 필터링</td>
      <td>그룹화 <strong>이후</strong>에 필터링</td>
    </tr>
    <tr>
      <td>사용 가능</td>
      <td>일반 컬럼 (기본값)</td>
      <td><strong>집계 함수 사용 가능</strong> (<code>SUM</code>, <code>COUNT</code> 등)</td>
    </tr>
    <tr>
      <td>주요 목적</td>
      <td>특정 행을 제외</td>
      <td>그룹 결과 중 조건에 맞는 그룹만 출력</td>
    </tr>
  </tbody>
</table>

### 예제
1. 고객별 주문한 책의 총 가격이 30,000원 이상인 고객의 ID와 총 금액을 구하시오.
```sql
select od.custid, sum(b.price) 
from orders od
join book b
on b.bookid = od.bookid
group by od.custid 
having sum(b.price) >= 30000;
```
2. 오류 문법
```sql
group by cs.name, avg(b.price)
```
**group by** 안에는 **집계함수**가 들어갈 수 없다.

## 문제

1. 책 이름(bookname)별 주문 수가 2건 이상인 책의 이름과 주문 건수를 구하시오.
```sql
select b.bookname, count(*) 
from orders od
join book b
on b.bookid = od.bookid
group by b.bookname;
```

2. 출판사별로 등록된 책의 수가 2권 이상인 출판사의 이름과 등록된 책 수를 구하시오.
```sql
select b.publisher, b.bookname, count(*) as 책수
from orders od
join book b
on b.bookid = od.bookid
group by b.publisher, b.bookname
having count(*) >= 2;
```

3. 고객 이름(name)별로 주문한 책의 평균 가격이 15,000원 이상인 고객 이름과 평균 가격을 구하시오.
```sql
select cs.name, avg(price)
from orders od 
join customer cs
on cs.custid = od.custid
join book b
on b.bookid = od.bookid
group by cs.name
having avg(price) >= 15000;
```

4. 책 ID(bookid)별로 해당 책을 주문한 서로 다른 고객 수가 2명 이상인 책 ID와 고객 수를 구하시오.
```sql
select od.bookid, count(distinct od.custid) as 고객수
from orders od 
group by od.bookid
having count(distinct od.custid) >= 2;
```

5. 주소(address)별로 고객이 주문한 총 도서 40,000원 이상인 주소와  가격합계를 구하시오.
```sql
select cs.address, sum(b.price)
from orders od
join customer cs
on cs.custid = od.custidd
join book b
on b.bookid = od.bookid
group by cs.address
having sum(b.price) >= 40000;
```

6. 출판사(publisher)별 평균 책 가격이 20,000원 이상인 출판사의 이름과 평균 가격을 구하시오.
```sql
select b.publisher, avg(b.price)
from orders od
join book b
on b.bookid = od.bookid
group by b.publisher
having avg(b.price) >= 20000;
```

7. 고객 ID별로 주문한 책 수가 1건뿐인 고객 ID만 출력하시오.
```sql
select custid, count(*)
from orders od
group by custid
having count(*) = 1;
```


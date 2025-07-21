---
layout: single
title: "Case"
excerpt: "Case 이해하기"
categories: OracleSQL
tag: OracleSQL
toc: true
---

## CASE

**CASE**는 조건에 따라 값을 다르게 출력할 수 있도록 해주는 조건 분기 표현식이다
프로그래밍 언어의 if, switch 문과 비슷한 역할을 하며, **SELECT문 내**에서 많이 사용된다

### 기본문법
```sql
SELECT 
  컬럼명,
  CASE
    WHEN 조건1 THEN 결과1
    WHEN 조건2 THEN 결과2
    ...
    ELSE 기본값
  END AS 별칭
FROM 테이블명;
```

### 예제
1. 고객별 주문 횟수를 구하고, 주문 횟수에 따라 
(‘우수고객’, ‘보통고객’, ‘일반고객’으로 등급을 나누어 고객이름과 함께출력하시오.)
```sql
select cs.name,
    case
        when count(*) >= 3 then '우수고객'
        when count(*) >= 2 then '보통고객'
        else '일반고객'
    END AS 회원등금,
    count(*) as 주문횟수
from customer cs
join orders od 
on cs.custid = od.custid
group by cs.name;
```

## 문제 
1. 도서 출판사별로 판매된 도서 수를 구하고, 
(5권 이상 판매된 출판사에는 ‘인기 출판사’, 아니면 ‘기타’라고 표시하시오.)
```sql
select b.publisher,
    case
        when count(*) >= 5 then '인기 출판사'
        else '기타'
    END AS 도서등급,
    count(*) as 도서수
from orders od
join book b
on b.bookid = od.bookid
group by b.publisher;
```

2. 고객 주소별 총 주문 금액을 구하고, 
(50,000원 이상인 주소는 ‘우수지역’, 아니면 ‘일반지역’으로 분류하시오.)
```sql
select
    cs.address,
    case
        when sum(b.price) >= 50000 then '우수지역'
        else '일반지역'
    end as 지역등급,
    sum(b.price)
from orders od
join customer cs
on cs.custid = od.custid
join book b
on b.bookid = od.bookid
group by cs.address;
```

3. 도서별 주문 수를 구하고, 
(10권 이상 주문된 도서는 ‘베스트셀러’, 아니면 ‘일반도서’로 표시하시오.)
```sql
select bookid, 
    case
        when count(*) >= 10 then '베스트셀러'
        else  '일반도서'
    end as 도서등급,
    count(*) as 주문수
from orders 
group by bookid;
```

4. 고객별로 주문한 책 가격의 평균을 구하고,
(평균 가격이 25,000원 이상인 고객은 ‘고가구매자’, 아니면 ‘일반구매자’로 구분하시오.)
```sql
 select cs.custid,
    case
        when avg(b.price) >= 25000 then '고가구매자'
        else '일반구매자'
    end as 고객등급,
    avg(b.price)
from orders od
join customer cs
on cs.custid = od.custid
join book b
on b.bookid = od.bookid
group by cs.custid;
```
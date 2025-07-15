---
layout: single
title: "OrcaleSQL 복습"
excerpt: "Oracle문법개념 복습"
categories: OracleSQL
tag: OracleSQL
toc: true
---

자바 개념 수업이 끝나고 오라클인지 미라클인지 어쩃든 뭔가를 또 배운다.  
😢😭😢😭😢😭😢😭😢😭😢😭😢😭😢😭😢😭😢😭😢😭😢😭

# OracleSQL
일단 잘 뭔지 모르니 찌피티한테 물어보자.  

```markdown
오라클 SQL은

오라클(Oracle) 데이터베이스에서 사용하는 **SQL(Structured Query Language)**을 의미해요.

즉,
**"오라클 DBMS에서 사용하는 표준 데이터 질의 언어(SQL)"**예요.
다른 DBMS(MySQL, PostgreSQL 등)와 기본 구조는 같지만,
오라클만의 **고유한 확장 기능(PL/SQL 등)**도 포함돼요.
```
그렇다고 알려준다......  
친절하게 구성요소 까지 알려준다 일단 모르지만 컨트롤CV해보자

```html
<table>
  <thead>
    <tr>
      <th>구분</th>
      <th>설명</th>
      <th>예시</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>DDL</td>
      <td>데이터 정의어</td>
      <td><code>CREATE</code>, <code>ALTER</code>, <code>DROP</code></td>
    </tr>
    <tr>
      <td>DML</td>
      <td>데이터 조작어</td>
      <td><code>SELECT</code>, <code>INSERT</code>, <code>UPDATE</code>, <code>DELETE</code></td>
    </tr>
    <tr>
      <td>DCL</td>
      <td>데이터 제어어</td>
      <td><code>GRANT</code>, <code>REVOKE</code></td>
    </tr>
    <tr>
      <td>TCL</td>
      <td>트랜잭션 제어어</td>
      <td><code>COMMIT</code>, <code>ROLLBACK</code>, <code>SAVEPOINT</code></td>
    </tr>
    <tr>
      <td>PL/SQL</td>
      <td>오라클 고유의 절차형 언어</td>
      <td><code>BEGIN...END</code>, 커서, 루프, 예외 등</td>
    </tr>
  </tbody>
</table>
```
일단 이렇다고 알려주는데 나중에 보면 이해될거다....아마..도  

그럼 오늘 배운거를 정리해보겠다.

## 계정생성

```sql
alter session set "_ORACLE_SCRIPT" = true;
--계정 이름 제약 해제
create user madang IDENTIFIED by 12345;
--madang 사용자 생성
grant connect, resource to madang;
--madang 사용자에게 권한 부여
grant create view, create sequence, create procedure to madang;
--madang 사용자에게 뷰 생성, 시퀀스 생성, 프로시져 생성 권한 부여
alter user madang default tablespace users quota unlimited on users;
--물리적 저장 고간
drop user madang;
--계정 삭제(실행x)
```
>>> 이렇게하면 madang 계정을 만들 수 있다.

--------------------------------------------------------------

## DDL(DATA DEFINITION LANGUAGES)

```sql
/*
create: 생성
drop: 삭제
alter:테이블 또는 권한 수정, 추가
*/

--책 테이블 생성(책 정보 저장)
create table book(
    bookid number primary key, ---기본키 : bookid
    bookname varchar2(40),
    pulisher varchar2(40),
    price number
);
--vachar2:문자열
--primary key(기본키_ 튜플(행)을 구분해 줄 수 있는 키
--number : 숫자데이터
select * from book;

--테이블 삭제
drop table book;
--------------------------------------------------------------------------------
--고객정보 테이블(고객정보 저장)
create table customer(
    custid number,
    name varchar2(20),
    address varchar2 (20),
    phone varchar2(20),
    primary key(custid)---기본키 : custid
);
select * from customer;

--판매정보 테이블
drop table orders;
create table orders(
    orderid number(10),
    orderdate date,
    custid number references customer(custid),
    bookid number references book(bookid),
    primary key(orderid)
);

select * from orders;
```
여기에서 중요한 부분이 바로 외래키예요:

✅ 외래키 1: custid references customer(custid)
orders 테이블의 custid는
customer 테이블의 custid 값을 참조해요!

즉, 주문을 넣으려면 존재하는 고객만 가능해요.
→ 없는 고객 ID는 넣을 수 없어요 ❌

✅ 외래키 2: bookid references book(bookid)
orders 테이블의 bookid는
book 테이블의 bookid 값을 참조해요!

즉, 주문하려면 존재하는 책이어야 해요.
→ 없는 책 ID도 주문 불가 ❌ 

### 외래키 좀더 쉽게 이해하기

```html
<!-- 1. 고객 테이블 -->
<h3>1. 고객 테이블</h3>
<table border="1">
  <tr>
    <th>custid</th>
    <th>name</th>
  </tr>
  <tr>
    <td>1</td>
    <td>철수</td>
  </tr>
  <tr>
    <td>2</td>
    <td>영희</td>
  </tr>
</table>

<br>

<!-- 2. 책 테이블 -->
<h3>2. 책 테이블</h3>
<table border="1">
  <tr>
    <th>bookid</th>
    <th>bookname</th>
  </tr>
  <tr>
    <td>101</td>
    <td>자바 입문서</td>
  </tr>
  <tr>
    <td>102</td>
    <td>파이썬 기초</td>
  </tr>
</table>

<br>

<!-- 3. 주문 테이블 -->
<h3>3. 주문 테이블 (외래키 포함)</h3>
<table border="1">
  <tr>
    <th>orderid</th>
    <th>custid</th>
    <th>bookid</th>
  </tr>
  <tr>
    <td>1</td>
    <td>1</td>
    <td>101</td>
  </tr>
  <tr>
    <td>2</td>
    <td>2</td>
    <td>102</td>
  </tr>
</table>

```
✅ 결론
orderid = 1번 주문은
→ 철수(custid = 1) 가
→ 자바 입문서(bookid = 101) 를
→ 구매한 기록이라는 걸 알 수 있다.

✅ 결론
orderid = 2번은
→ 영희(custid 2) 가 
→파이썬 기초(bookid 102) 를
→ 구매한 기록이라는 걸 알 수 있다
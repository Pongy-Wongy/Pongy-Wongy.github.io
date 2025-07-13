---
layout: single
title: "여러가지 코드로 입출금시스템 만들기"
excerpt: "switch-case문, do-while문, for문 으로 만드는 은행 입출금 시스템입니다."
categories: Java
tags: Java
toc: true
---

## Switch-case

```java
package chapter03;

import java.util.Scanner;

public class Example08 {
	
	public static void main(String[] args) {
		
		Scanner scan = new Scanner(System.in);
		int account = 0;//은행계좌
		int num;
		boolean run = true;
				
		while (run) {
			System.out.println("=============");
			System.out.println("1.입금하기 || 2. 출금하기 3. 종료하기");
			System.out.println("번호를 입력하세요");
			num = Integer.parseInt(scan.nextLine());
			
			switch (num) {
			case 1:{
				System.out.println("1.입금하기를 선택하셨습니다");
				System.out.println("입금할 금액을 입력하세요 >>");
				int input = Integer.parseInt(scan.nextLine());
				account += input;
				System.out.println("현재 계좌에 남은 금액 :" + account);
				break;
			}
			case 2:{
				System.out.println("1.출금하기를 선택하셨습니다");
				
				System.out.println("출금할 금액을 입력하세요 >>");
				int output = Integer.parseInt(scan.nextLine());
				if (account < output) {
					System.out.println("잔액이 부족합니다!!");
				}//유지보수 : 잔고가 출ㄹ금할 금액보다 큰 상황
				account -= output;
				System.out.println("현재 계좌에 남은 금액 :" + account);
				break;
			}
			case 3:{
				System.out.println("1.종료하기를 선택했습니다");
				run = false;
				break;
			}
			default:
				System.out.println("잘못된 번호를 입력하셨습니다");
				break;
			}//switch
		
		}//while
		System.out.println("당신의 계좌의 현재 금액은" + account + "입니다");
				
		}
	}

```


## do-while 

```java
    import java.util.Scanner;

public class while01 {
    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);
        int account = 0; // 은행 계좌
        int num;
        int amount;

        do {
            System.out.println("==========================");
            System.out.println("1. 입금하기 | 2. 출금하기 | 3. 종료하기");
            System.out.print("번호를 입력하세요 >>> ");
            num = Integer.parseInt(scan.nextLine());

            if (num == 1) {
                System.out.print("입금할 금액을 입력하세요 >>> ");
                amount = Integer.parseInt(scan.nextLine());
                account += amount;
                System.out.println("현재 계좌에 남은 금액 : " + account + "원");

            } else if (num == 2) {
                System.out.print("출금할 금액을 입력하세요 >>> ");
                amount = Integer.parseInt(scan.nextLine());

                if (account < amount) {
                    System.out.println("잔액이 부족합니다!!");
                } else {
                    account -= amount;
                    System.out.println("현재 계좌에 남은 금액 : " + account + "원");
                }

            } else if (num == 3) {
                System.out.println("3. 종료하기를 선택했습니다.");
            } else {
                System.out.println("잘못된 번호입니다. 다시 선택해주세요.");
            }

        } while (num != 3); // 3을 입력하면 종료

        System.out.println("종료합니다. 최종 잔액은 " + account + "원입니다.");
        scan.close();
    }
}

```

## for문

```java
import java.util.Scanner;

public class forBankSys {
    public static void main(String[] args) {

        Scanner scan = new Scanner(System.in);
        int account = 0; // 은행 계좌
        int amount;

        for (int i = 1; i <= 3; i++) {
            System.out.println("1. 입금하기 | 2. 출금하기 | 3. 종료하기");
            System.out.print("번호를 입력하세요 >>> ");
            i = Integer.parseInt(scan.nextLine());
            if (i == 1) {
                System.out.print("입금할 금액을 입력하세요 >>> ");
                amount = Integer.parseInt(scan.nextLine());
                account += amount;
                System.out.println("현재 계좌에 남은 금액 : " + account + "원");

            } else if (i == 2) {
                System.out.print("출금할 금액을 입력하세요 >>> ");
                amount = Integer.parseInt(scan.nextLine());

                if (account < amount) {
                    System.out.println("잔액이 부족합니다!!");
                } else {
                    account -= amount;
                    System.out.println("현재 계좌에 남은 금액 : " + account + "원");
                }

            } else if (i == 3) {
                System.out.println("3. 종료하기를 선택했습니다.");
            } else {
                System.out.println("잘못된 번호입니다. 다시 선택해주세요.");
            }
        }//for문
        System.out.println("종료합니다. 최종 잔액은 " + account + "원입니다.");
    }
}

```
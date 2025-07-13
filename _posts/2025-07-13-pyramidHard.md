---
layout: single
title: "중첩for문-피라미드(심화)"
excerpt: "피라미드(심화)로 중첩for문 복습"
categories: Java
tags: Java
toc: true
---

## 공백 있는 피라미드 쌓기!
```java
public class for01 {
    public static void main(String[] args) {

        int height = 5;//피라미드 높이

        for(int i=0; i<height; i++) {

            //1.공백
            for(int j=0; j<height -i -1; j++) {
                System.out.print(" ");
            }
            //2. 별 출력
            for(int k=0; k<(2*i+1); k++) {
                System.out.print("*");
            }
            System.out.println();
        }//외부 for문
    }
}
```
```java
public class for {
    public static void main(String[] args) {
       int rows = 5;

       for (int i=1; i <=rows; i++) {
           for(int j=1; j<=rows-i; j++) {
               System.out.print(" ");
           }
           for (int k = 1; k <= (2*i-1); k++) {
               System.out.print("*");
           }
           System.out.println();
       }//외부 for문
    }
}
```

위 의 2개 코드는 출력값이 같지만 작성 식이 틀리다. 

### 출력 값
```java
    *       ← 1번째 줄 (공백4개 + 별1개)
   ***      ← 2번째 줄 (공백3개 + 별3개)
  *****     ← 3번째 줄 (공백2개 + 별5개)
 *******    ← 4번째 줄 (공백1개 + 별7개)
*********   ← 5번째 줄 (공백0개 + 별9개)

```

```java
| 줄 번호 | `i` 값(for1: `i=0~4`) | `i` 값(for02: `i=1~5`) | 공백 수 | 별 수 | 출력 결과       |
| ---- | ------------------------ | ------------------------- | ---- | --- | ----------- |
| 1    | 0                        | 1                         | 4    | 1   | `    *`     |
| 2    | 1                        | 2                         | 3    | 3   | `   ***`    |
| 3    | 2                        | 3                         | 2    | 5   | `  *****`   |
| 4    | 3                        | 4                         | 1    | 7   | ` *******`  |
| 5    | 4                        | 5                         | 0    | 9   | `*********` |

```

*결국 중요한거는 몇 번 반복이고 외부for문과 내부for문의 구조? 순서? 를 잘 이해해야 있다.*
# UVA11332：Summing Digits

## 題目概要

- 所有位數相加直至剩下個位數。

- 當 n = 0 時結束程式。

## 解題技巧

- input 為小於 2,000,000,000 的正整數，超出 int 範圍所以用 long。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        long n = sc.nextLong();
        if (n == 0) break;
        while(n / 10 != 0) n = n / 10 + n % 10;
        System.out.println(n);
    }
  }
};
```

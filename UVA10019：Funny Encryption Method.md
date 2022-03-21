# UVA10019：Funny Encryption Method

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=24&page=show_problem&problem=960)

## 題目概要

- 將輸入的數值視為十進位及十六進位，分別計算出轉換成二進位後有多少個 1。

## 解題技巧

- 用 `Integer.toBinaryString` 來將十進位轉為二進位

- 先用 `Integer.parseInt("" + number, 16)` 將十進位轉為十六進位，再轉換成二進位。

- 用 for 迴圈遍歷計算有多少個 1。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class Uva10019 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        int number = sc.nextInt();
        String x = Integer.toBinaryString(number);
        String y = Integer.toBinaryString(Integer.parseInt("" + number, 16));
        int xCount = 0;
        int yCount = 0;
        for(int i = 0; i < x.length(); i++) {
            if (x.charAt(i) == '1') xCount++;
        }
        for(int j = 0; j < y.length(); j++) {
            if (y.charAt(j) == '1') yCount++;
        }
        System.out.println(xCount + " " + yCount);
    }
  }
};
```

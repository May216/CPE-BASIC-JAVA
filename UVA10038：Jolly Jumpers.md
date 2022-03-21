# UVA10038：Jolly Jumpers

[Online Judge](https://onlinejudge.org/index.php?option=onlinejudge&Itemid=8&page=show_problem&problem=979)

## 題目概要

- 每一行都是一筆測資

- 每筆測資的第一個數字代表該測資總共有 N 個數字

- 計算相鄰相數的差值，若最後差值為 1 ~ N 就輸出 `Jolly`，反之則輸出 `Not jolly`

## 解題技巧

- 用一個 array 來記錄所有差值，輸入的數字 <= 3000 所以將長度設為 3001。

- 相鄰兩數差值紀錄可以寫成 `diff[Math.abs(number[i] - number[i - 1])] = true;`，也就是說差值為 array 中為 true 的 index。

- 最後用一個 1 ~ n 的 for 迴圈，假如 array[1] ~ array[n] 有不為 true 的值，就輸出 `Not jolly`，否則輸出 `Jolly`

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class Uva10038 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int n = sc.nextInt(); // 多少個數字
        int number[] = new int[n];
        boolean diff[] = new boolean[3001];

        number[0] = sc.nextInt();
        for (int i = 1; i < n; i++) {
            number[i] = sc.nextInt();
            diff[Math.abs(number[i] - number[i - 1])] = true;
        }

        boolean flag = true;
        for (int j = 1; j < n; j++) {
            if (!diff[j]) flag = false;
        }

        if (flag) System.out.println("Jolly");
        else System.out.println("Not jolly");
    }
  }
};
```

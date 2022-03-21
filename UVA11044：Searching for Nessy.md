# UVA11044：Searching for Nessy

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1985)

## 題目概要

- 輸入 N 筆測資

- 輸入 M * N 的矩形，並計算這個舉行中可以放多少個 3 * 3 的矩形。

## 解題技巧

- 無

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        int m = sc.nextInt();
        int n = sc.nextInt();
        System.out.println((m / 3) * (n / 3));
    }
  }
};
```

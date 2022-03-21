# UVA11172：Relational Operators

[Online Judge](https://onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=2113)

## 題目概要

- 輸入 N 筆測資

- 輸入 X, Y 並判斷 X 和 Y 的大小關係

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
        int x = sc.nextInt();
        int y = sc.nextInt();
        if (x > y) System.out.println('>');
        else if (x < y) System.out.println('<');
        else System.out.println('=');
    }
  }
};
```

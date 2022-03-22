# UVA10783：Odd sum

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=19&page=show_problem&problem=1724)

## 題目概要

- 輸入 N 筆測資。

- 計算 X, Y 之間存在的奇數總和。

## 解題技巧

- 判斷是否為奇數只需要將數值除以2，不餘 0 的數值就是奇數。

## 程式碼

```java
import java.util.Scanner;
public class Uva10783 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    int id = 0;
    while (cases-- > 0) {
      id++;
      int x = sc.nextInt();
      int y = sc.nextInt();
      int sum = 0;
      for(int i = x; i <= y; i++) {
        if (i % 2 != 0) sum += i;
      }
      System.out.println("Case " + id + ": " + sum);
    }
  }
}
```

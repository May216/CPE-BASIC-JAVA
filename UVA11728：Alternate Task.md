# UVA11728：Alternate Task

## 題目概要

- 給定正整數 S，找到一個因數加起來等於 S 的數字。

- 每組測資一行，每一行有一個正整數S (S ≤ 1000)。 如果S = 0代表輸入結束。

- 對於每組測資，輸出測資編號，接著輸出其因數和等於S的答案數字。如果存在多組，請輸出其中最大的整數。 如果不存在，請輸出"-1"。

## 解題技巧

- 從 S 開始倒著找，找到哪個數的因數加總和 S 一樣大。

## 程式碼

```java
import java.util.*;
public class main {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int n;
    int cases = 1;
    while (sc.hasNextInt() && (n = sc.nextInt()) != 0) {
      for (int i = n; i > 0; i--) {
        Vector<Integer> vector = new Vector<Integer>();
        int temp = i;

        //找出某數的因數
        int j = 1;
        while (j <= temp) {
          if (temp % j == 0) vector.add(j);
          j++;
        }

        //因數加總
        Iterator<Integer> iterator = vector.iterator();
        int sum = 0;
        while (iterator.hasNext()) {
          sum = sum + iterator.next();
        }

        if (n == sum) {
          System.out.println("Case " + cases + ": " + i);
          break;
        }

        if (i == 1) System.out.println("Case " + cases + ": -1");
      }
      cases++;
    }
  }
}
```

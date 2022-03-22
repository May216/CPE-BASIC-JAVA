# UVA11312：Sort! Sort!! and Sort!!!

## 題目概要

- 給你兩個整數 N (0<N<=10000), M (0<M<=10000)，你要依照某些規則排序 N 個整數。

- 先利用每個數字除以M的餘數由小到大排，若排序中比較的兩數為一奇一偶且兩數除以M 的餘數相等，則奇數要排在偶數前面。若兩奇數除以M餘數大小相等，則原本數值較大的奇數排在前面。同樣的，若兩偶數除以M餘數大小相等，則較小的偶數排在前面。

- 餘數相等：
  
  1. 一奇一偶：奇數要排在偶數前面
  2. 兩奇數：原本數值較大的奇數排在前面
  3. 兩偶數：較小的偶數排在前面

## 解題技巧

- 餘數由小到大排 (-divisor + 1 ~ divisor - 1)，奇數由大到小輸出 `int j = arr.size() - 1; j >= 0; j--`，偶數由小到大輸出 `int j = 0; j < arr.size(); j++`

## 程式碼

```java
import java.util.*;
public class Uva11321 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextInt()) {
      int n = sc.nextInt(), divisor = sc.nextInt();
      System.out.println(n + " " + divisor);
      if(n == 0 && divisor == 0) break;

      Vector<Integer> arr = new Vector<Integer>();
      for(int i = 0; i < n; i++) arr.add(sc.nextInt());

      Collections.sort(arr);
      // 餘數小到大 (-divisor + 1 ~ divisor - 1)
      for(int i = (0 - divisor + 1); i < divisor; i++) {
        // 奇數大到小
        for(int j = arr.size() - 1; j >= 0; j--) {
          int number = arr.get(j);
          if(Math.abs(number) % 2 == 1 && number % divisor == i) {
            System.out.println(number);
          }
        }
        // 偶數小到大
        for(int j = 0; j < arr.size(); j++) {
          int number = arr.get(j);
          if(Math.abs(number) % 2 == 0 && number % divisor == i) {
            System.out.println(number);
          }
        }
      }
    }
  }
}
```

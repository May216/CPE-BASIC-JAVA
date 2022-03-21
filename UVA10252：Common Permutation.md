# UVA10252：Common Permutation

## 題目概要

- 給定兩個由小寫字母組成的字串a和b。印出最長的小寫字串x，使得x經過重新排列後為a的子序列，且x經過重新排列後為b的子序列。

- 連續的兩行為一組，第一行為字串a，第二行為字串b，1~2行為一組輸入，3~4行為一組輸入，依此類推。每個字串最多包涵1000個小寫字母。

- 對於每組輸入，輸出本題要求a和b的x，如果有多組符合的x，請印出字母順序由小到大排列的那一個。

## 解題技巧

- 若 a 有三個 e，但 b 只有兩個 e，最後結果須取最短的那個，輸出 ee。

## 程式碼

```java
import java.util.*;
public class Uva10252 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextLine()) {
      String a = sc.nextLine(), b = sc.nextLine();
      int c1[] = new int[123];
      int c2[] = new int[123];

      for(int i = 0; i < a.length(); i++) {
        c1[a.charAt(i)]++;
      }
      for(int i = 0; i < b.length(); i++) {
        c2[b.charAt(i)]++;
      }

      for(int k = 97; k <= 122; k++) {
        for(int n = 0; n < Math.min(c1[k], c2[k]); n++) System.out.print((char) k);
      }
      System.out.println("");
    }
  }
}
```

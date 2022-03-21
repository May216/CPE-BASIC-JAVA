# UVA10260：Soundex

## 題目概要

- 根據題目中的對照表，將字母轉換成數字，並且不轉換 A,E,I,O,U,H,W,Y 這幾個英文字母。

- 對照表：
  
  1 represents B, F, P, or V
  2 represents C, G, J, K, Q, S, X, or Z
  3 represents D or T
  4 represents L
  5 represents M or N
  6 represents R

- 一筆測資最多可以有 20 個字母。

- 當連續兩個數字相同時，只保留一個，例如122353 => 12353。

## 解題技巧

- 用 `str.replaceAll` 使用正則的方式將匹配到的字母轉換成相對應的數字。

- 用 `String.format("%d+", i)` 的方式來判斷是否有連續相同的數字，如果有，就將連續的數字只保留一個。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        String str = sc.next();
        str = str.replaceAll("[BFPV]", "1");
        str = str.replaceAll("[CGJKQSXZ]", "2");
        str = str.replaceAll("[DT]", "3");
        str = str.replaceAll("[L]", "4");
        str = str.replaceAll("[MN]", "5");
        str = str.replaceAll("[R]", "6");
        for (int i = 1; i <= 6; i++) {
            String regex = String.format("%d+", i);
            str = str.replaceAll(regex, Integer.toString(i));
        }
        str = str.replaceAll("[AEIOUHWY]", "");
        System.out.println(str);
    }
  }
};
```

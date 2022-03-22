# UVA10812：Beat the Spread!

## 題目概要

- 輸入 N 筆測資，每筆測資包含 s, d 兩個正整數，s 為比賽結束時兩隊分數的總和，d 代表比賽結束時兩隊分數差的絕對值。

## 解題技巧

- 比分高的計算方式為 $(s + d) / 2$，比分低的計算方式為 $(s - d)/2$，如果除完不是整數就輸出 impossible。

- 總和不可能比相差的分數還小，所以如果 s < d 是錯的。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        int s = sc.nextInt(), d = sc.nextInt();
        if (s < d || (((s + d) % 2) != 0) || (((s - d) % 2) != 0)) System.out.println("impossible");
        else {
            System.out.println(((s + d) / 2) + " " + ((s - d) / 2));
        }
    }
  }
};
```

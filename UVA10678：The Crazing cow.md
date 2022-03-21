# UVA10678：The Crazing cow

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1619)

## 題目概要

- 一頭牛在田野裡吃草，田野裡有一根繩子用兩根柱子繫著， 牛被的鼻子被繩子穿過，我們需要計算出牛可以吃草的區域範圍大小。
- 輸入 N 筆測資。
- 接著輸入 D, L。
  - D 表示兩根柱子之間的距離 (0 ≤ D ≤ 1000)
  - L 為繩索長度 (D < L ≤ 1500)
- 請使用雙精度浮點數據類型進行浮點計算(double)。
- 需輸出到**小數點後三位**。

## 解題技巧

- 以**橢圓**的概念解題，焦點為牛的鼻子，橢圓面積公式 `PI * a * b`
- c = D/2, a = L/2，根據畢氏定理換算 `b^2 = a^2 - c^2` 開根號拿到 b，如此一來我們就能獲取到 a, b, c 的長度。
- 再以橢圓面積公式 `PI * a * b` 計算出牛的吃草面積。
- PI 可用 Math.PI 獲取：`final double PI = Math.PI; // Math.PI 也可以寫成 acos(-1);`

以第一筆測資為例，兩根柱子距離 10 英尺(D)，12 英尺的繩子(L)，計算出 c = 5, a = 6, b = 根號11，3.14 * 6 * 根號11 => $3.3166247 * 3.1415926 * 6$ 取小數點後三位則四捨五入為 `62.517`。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class Uva10678 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        final double PI = Math.PI;
        int D = sc.nextInt(), L = sc.nextInt(); // D:柱子距離, L:繩子長度

        double a = L/2.0, c = D/2.0; // 以雙精度浮點數計算
        double b = Math.sqrt(Math.pow(a,2) - Math.pow(c,2)); // b^2 = a^2 - c^2

        double result = PI * a * b; // 橢圓面積

        System.out.printf("%.3f", result); // 取小數點後三位
        System.out.println("");
    }
  }
};
```

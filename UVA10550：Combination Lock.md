# UVA10550：Combination Lock

[Online Judge](https://onlinejudge.org/index.php?option=onlinejudge&page=show_problem&problem=1491)

## 題目概要

- 給定刻度盤的初始位置和鎖的組合，請計算出打開鎖時總共旋轉了多少度（順時針加逆時針）。
- 每筆測資，都包含 4 個數字(0和39)，第一個數字是錶盤的位置，接下來的三個數字是組合。
- 這鎖有一個帶有 40 個刻度的刻度盤，編號為 0 到 39。
- 組合由這些數字中的隨機 3 個組成； 例如：15-25-8。
- 若為 0 0 0 0 則結束。
- 要打開鎖，需要執行以下步驟：
  - 1.順時針轉 2 圈
  - 2.順時針轉到第一個數字
  - 3.逆時針轉 1 圈
  - 4.逆時針轉到第二個數字
  - 5.順時針轉到第三個數字
  - 6.成功解鎖。

## 解題技巧

- 每圈為 360 度，一圈 360 度共 40 個刻度，所以轉一個刻度為 9 度。
- 順時針轉為 0,39,38,37....，逆時針轉為 0,1,2,3,4,5....
- 看兩數之間是大到小還是小到大判斷是順時針轉還是逆時針轉，如果順時針時 `a >= b` 則`a-b * 9`，否則 `40+a-b * 9`；若是逆時針時 `a >= b` 則 `40+a-b * 9`，否則 `a-b*9`。
- 以第一筆測資( 0 30 0 30 )為例，首先順時針轉 2 圈加逆時針轉 1 圈 = 1080 度，接著再順時針轉從 0(40) ~ 30 => 10 * 9 = 90 度，再順時針從 30 ~ 0 => 10 * 9 = 90 度，最後順時針從 0(40) ~ 30 => 10 * 9 = 90 度，答案為 1080 + 90 + 90 + 90 = 1350 度。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()){
        int a = sc.nextInt(),b = sc.nextInt(),c = sc.nextInt(),d = sc.nextInt();
        if (a == 0 && b == 0 && c == 0 && d == 0) break;
        int degree = 1080; // 2 * 360 + 1 * 360 = 1080
        int scale = 360 / 40;
        degree += (a >= b) ? (a - b) * scale : (40 + a - b) * scale; // 順時針 0 -> 30
        degree += (b <= c) ? (c - b) * 9 : (40 + c - b) * 9; // 逆時針 30 -> 0
        degree += (c >= d) ? (c - d) * scale : (40 + c - d) * scale; // 順時針 0 -> 30

        System.out.println(degree);
    }
  }
};
```

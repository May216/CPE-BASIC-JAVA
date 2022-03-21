# UVA10056：What is the Probability?

## 題目概要

- 輸入 N 筆測資，每筆測資有三個數，第一個數為參加遊戲的人數，第二個數為獲勝機率，第三個數為第幾個人獲勝，計算出獲勝者的機率。

## 解題技巧

- 若獲勝機率為 p，輸的機率就會是 q = 1 - p，每次遊戲共有 R 個回合，有 n 個人參與遊戲，第 k 個人獲勝。
  
  - **第一輪**：第一個人獲勝機率 p；第二個人獲勝機率 q * p；第三個人獲勝機率 $q^2 * p$，代表第 k 個人獲勝機率為 $q^(k-1) * p$
  
  - **第二輪**：第一個人獲勝機率 $(q^n) * p$；第二個人獲勝機率 $(q^n) * q * p$；第三個人獲勝機率 $(q^n)*(q^2)*p$，代表第 k 個人獲勝機率為 $(q^n)*(q^(k-1))*p$
  
  - **第 R 輪**：第一個人獲勝機率 $(q^(R-1)*n) * p$；第二個人獲勝機率 $(q^(R-1)*n) * q * p$；第三個人獲勝機率 $(q^(R-1)*n) * (q^2) * p$，代表第 k 個人獲勝機率為 $(q^(R-1)*n) * (q^(k-1)) * p$
  
  - 整理後的公式為：(q^(k-1)*p) * (1-(q^n^R)) / (1-q^n) ，首項：$(q^(k-1)*p)$、公比：$q^n$

- 使用等比數列公式計算：$S = a(1-r^n)/1-r$，S 為和，a 為首項，r 為公比，n 為次數。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    int R = 50; // 回合數
    while(cases-- > 0) {
        int n = sc.nextInt(); // 遊玩人數
        double p = sc.nextDouble(), q = 1 - p; // p: 獲勝機率 q: 輸掉機率
        int k = sc.nextInt(); // 第 k 個人獲勝

        double a = Math.pow(q, k - 1) * p; // 首項
        double r = Math.pow(q, n); // 公比

        if(p == 0) System.out.println("0.0000");
        else System.out.printf("%.4f\r\n", a * (1 - Math.pow(r, R)) / (1 - r));
    }
  }
};
```

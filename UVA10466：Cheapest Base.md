# UVA11005：Cheapest Base

## 題目概要

- 使用 0~9 , A ~Z 來表示進制中使用到的字元，最大進制為 36 (0 ~ Z)，最小為 2 (0, 1)，請計算出可表達此數的最小墨水量以及其進制為多少。

- 第一行為測資數 N，每一組側資包含：4 * 9 = 36 個數字，分別對應 0~9 , A~Z 的墨水量，再接下來會跟著一個正整數 F，代表要查詢的數字個數，接下來 F 行為要查詢的數字。

## 解題技巧

- 10進制要轉成 2 ~ 36 進制可以使用短除法。

- 用長度 36 的一維陣列來儲存對應的墨水量。

- 當查詢的數字除以 制數取餘數後，該餘數為墨水量陣列的索引值。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt();
    for(int i = 1; i <= n; i++) {
        System.out.printf("Case %d:\r\n", i);
        // 存墨水量
        int ink[] = new int[36];
        for(int j = 0; j < ink.length; j++) ink[j] = sc.nextInt();

        int queries = sc.nextInt();
        for(int j = 0; j < queries; j++) {
            int number = sc.nextInt();
            System.out.printf("Cheapest base(s) for number %d:", number);

            int min = Integer.MAX_VALUE;
            int cost[] = new int[37];

            for(int base = 2; base <= 36; base++) {
                int target = number;
                while(target > 0) {
                    int position = target % base; // 餘數對應墨水成本陣列索引
                    cost[base] += ink[position];
                    target /= base; // 取商
                }

                if(cost[base] < min) min = cost[base];
            }
            // 找出最小成本
            for(int base = 2; base <= 36; base++) {
                if (cost[base] == min) System.out.print(" " + base);
            }
            System.out.println();
        }
        if(i != n) System.out.println();
    }
  }
};
```

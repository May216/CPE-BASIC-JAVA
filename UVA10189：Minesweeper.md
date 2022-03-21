# UVA10189：Minesweeper

https://onlinejudge.org/external/101/10189.pdf

## 題目概要

- 踩地雷題目，需要你統計相鄰的地雷數。

- 踩地雷中的數字代表九宮格之內有幾個地雷。

- 測資第一行有兩個正整數 n, m， n 為列數 m 為行數，即為 n * m 的地圖。接下來會有 n * m 的字元，代表每一格的資料，若是 `*` 代表地雷，`.`代表可以踩的地方。

- 我們需要把 `.` 可以踩的地方轉成周圍地雷的數量再輸出。

- 當 n == 0 && m == 0 時終止。

![](C:\Users\user\Desktop\minesweeper.png)

## 解題技巧

- 用二維陣列儲存地圖，當檢查到地圖中的 * 時將周圍九宮格都 + 1。

- 如果 n * m 中任一位置的數超過 8 ，代表該位置為地雷。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = 0;
    while(sc.hasNext()) {
        int n = sc.nextInt(), m = sc.nextInt();
        if(n == 0 && m == 0) break;

        // 取得地圖內容
        int counts[][] = new int[n][m]; // 記錄地雷數
        for(int h = 0; h < n; h++) {
            String line = sc.next(); // 一列一列讀取
            for(int w = 0; w < m; w++) {
                char chr = line.charAt(w); // 抓取每列的每個字元

                // 統計地雷數
                if(chr == '*') {
                    // 地雷為 9
                    counts[h][w] = 9;
                    // 地雷周圍的開始與結束座標
                    int n1 = h - 1, n2 = h + 1; // 上下
                    int m1 = w - 1, m2 = w + 1; // 左右

                    for(int l = n1; l <= n2; l++) {
                        for(int r = m1; r <= m2; r++) {
                            // 判斷是否超出範圍
                            if (l >= 0 && l < n && r >= 0 && r < m) {
                                // 周圍九宮格地雷數 + 1
                                counts[l][r] += 1;
                            }
                        }
                    }
                }
            }
        }
        if (cases != 0) System.out.println();
        cases++;
        System.out.printf("Field #%d:\r\n", cases);

        // output
        for(int i = 0; i < n; i++) {
            for(int j = 0; j < m; j++) {
                 int count = counts[i][j];
                 if(count > 8) System.out.print("*");
                 else System.out.print(count);
            }
            System.out.println();
        }
    }
  }
};
```

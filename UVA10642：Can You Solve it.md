# UVA10642：Can You Solve it

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=24&page=show_problem&problem=1583)

## 題目概要

- 輸入 N 筆測資。

- 分別輸入第一個點的位置 (X1, Y1) 及第二個點的位置 (X2, Y2)。

- 根據圖上的規律，計算出從第一個位置到第二個位置需要經過幾個點。

## 解題技巧

- 這個圖的 x , y 軸是反過來的，要注意不要看錯了。

- x + y 能得知在第幾條線上，每條線上的點個數為 `x + y + 1`

- 先計算從 (0,0) 到第二個點所經過的點個數，再減去從 (0,0) 到第一個點所經過的點個數就能獲得答案。

- 我們可以先以求和公式 $(n*(n+1))/2$ 來計算出從 (0,0) 到第二個點總共需要多少個點，再減去 y (因為求和公式會連第二個點所在那條線的所有個數都加上，所以要減 y)，算出個數後，以同樣的方法再去算從 (0,0) 到第一個點經過的點的個數，兩者相減即為答案。(因為一樣的步驟做兩次，所以直接寫成一個 class `sum` 來處理)

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class Uva10642 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
       int cases = sc.nextInt();
       int count = 0;
       while(cases-- > 0) {
           count++;
           int x1 = sc.nextInt(), y1 = sc.nextInt(), x2 = sc.nextInt(), y2 = sc.nextInt();
           int answer = sum(x2, y2) - sum(x1, y1);
           System.out.println("Case " + count + ": " + answer);
       }
  }

  public static int sum(int x, int y) {
      int n = x + y + 1;
      return (((n * (n + 1)) / 2) - y);
  }
};
```

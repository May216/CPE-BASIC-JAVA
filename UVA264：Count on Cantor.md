## UVA264：Count on Cantor

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=200)

## 題目概要

![Count on Cantor.png](C:\Users\user\Desktop\Count%20on%20Cantor.png)

- 輸入 X ，根據上圖中的金字塔規律計算出第 X 個數是多少。

- 金字塔斜著看算一行，每行都比上一行再多一個數，第幾行就有幾個數。

- 從第二行開始看，**偶數行分子由小到大，奇數行分子由大到小。分母則是倒過來。**

- 順序為：1/1 -> 1/2, 2/1 -> 3/1, 2/2, 1/3 -> 1/4, 2/3, 3/2, 4/1 -> 5/1 ... 等，假設輸入 6 就要輸出 `1/3`。

## 解題技巧

- 首先計算出 X 這個數在第 i 行，且從第一行到第  **i**  行共有  **sum**  個數字。

- **偶數行分子由小到大，奇數行分子由大到小。分母則是倒過來。** 所以我們需要計算 sum 跟 X 的個數差 (diff)。

- 如果是偶數行，n 的結果就為 `(i - diff) / (1 + diff)` 反之則是 `(1 + diff) / (i - diff)`。

- 假設 n 為 7，7 > 6 且 7 < 10，所以 7 在第四行(i)，且第四行為偶數(i % 2 == 0)，因此分子是由小到大，第一到第四行總共有 10(sum) 個數，第一行至第四行最後一個數的總和跟第一行到第 n 個數的差值為 10 - 7 = 3 (diff)，可以計算出答案為 (4 - 3) / (1 + 3) = 1 / 4。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextInt()){
        int n = sc.nextInt();

        int i = 2;
        int sum = 1;
        while(sum < n){
            sum = sum + i;
            i++;
        }

        i--; // while 多算一次

        int diff = sum - n; // 從第一層到 n 所在那個斜排總共的數減去 n 算出差值
        if(i % 2 == 0) System.out.println("TERM " + n + " IS " + (i - diff) + "/" + (1 + diff));
        else System.out.println("TERM " + n + " IS " + (1 + diff) + "/" + (i - diff));
    }
  }
};
```

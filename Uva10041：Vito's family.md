# Uva10041：Vito's family

[Online Judge](https://onlinejudge.org/index.php?option=onlinejudge&Itemid=8&page=show_problem&problem=982)

## 題目概要

- 輸入 N 筆測資。

- 每筆測資的第一個數字為該筆測資總共有 X 個數字。

- 找出距離每個點都最近的點 M，並計算出其他點跟 M 相差的距離總和。

## 解題技巧

- 距離每個點皆最近的點 M 就是這些數字中的**中位數**。

- 首先將所有的數字存在一個 array 中並且按照順序排好，這樣就能直接透過 array 長度除以 2 來獲取中位數。

- 再用 for 迴圈遍歷計算每個點與中位數相差的距離相加起來就是答案。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class Uva10041 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        int n = sc.nextInt();
        int arr[] = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        Arrays.sort(arr);

        int sum = 0;
        int mid = arr[arr.length / 2]; // 中位數
        for (int i = 0; i < arr.length; i++) {
            sum += Math.abs(arr[i] - mid);
        }
        System.out.println(sum);
    }
  }
};
```

# UVA10714：Ants

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1655)

## 題目概要

- 每隻螞蟻可以往左或往右，兩隻螞蟻相遇時就會掉頭，螞蟻走到盡頭會掉下繩子，計算需要最慢與最快多久時間繩子上的螞蟻會全部掉光。
* 輸入：**1. cases 筆測資 2. 繩子長度 length 3. 螞蟻數量 number**

## 解題技巧

- 最近距離 min, 最遠距離 max, 螞蟻位置 position
- 最遠距離 = 走到距離當前位置最遠的端點距離
- 最近距離 = 走到距離當前位置最近的端點距離
- **最小值**：取出每個螞蟻的最小距離中的最大值
- **最大值**：取出每個螞蟻的最遠距離中的最大值

下方示意圖以第一筆測資為例：

```java
// input
10 3  (繩子長度為10, 有 3 隻螞蟻)
2 6 7 (螞蟻的位置分別為 2,6,7)
// output
4 8 (最小值:4, 最大值:8)
```

## 程式碼

```java
import java.util.Scanner;

/**
 * 每隻螞蟻可以往左或往右，兩隻螞蟻相遇時就會掉頭，螞蟻走到盡頭會掉下繩子，計算需要最慢與最快多久時間繩子上的螞蟻會全部掉光。
 * 輸入：1. cases 筆測資, 2. 繩子長度 length, 3. 螞蟻數量 number
 * 最近距離 min, 最遠距離 max, 螞蟻位置 position
 * 最遠距離 = 走到距離當前位置最遠的端點距離
 * 最近距離 = 走到距離當前位置最近的端點距離
 */
public class Uva10714 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();

    while (cases-- > 0) {
      int length = sc.nextInt(); // 繩子長度
      int number = sc.nextInt(); // 有幾隻螞蟻
      int min = 0, max = 0;

      while (number-- > 0) {
        int position = sc.nextInt(); // 每個螞蟻的位置
        position = position < length - position ? position : length - position; // 找出最小距離
        if (position > min) // 取出最小距離中的最大值
          min = position;
        if (length - position > max) // 找出最遠距離
          max = length - position;
      }
      System.out.println(min + " " + max);
    }
  }
}
```

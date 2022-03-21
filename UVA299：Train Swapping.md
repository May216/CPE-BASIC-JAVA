# UVA299：Train Swapping

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=24&page=show_problem&problem=235)[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=24&page=show_problem&problem=235)

## 題目概要

- 輸入 N 筆測資。

- 輸入該筆測資有幾節車廂。

- 計算出需要交換 X 次才能讓車廂號碼由小到大排序，只能相鄰兩節車廂交換。

## 解題技巧

- 最簡單就是用**泡沫排序法**，倆倆比較，如果左數比右數大就將兩數交換。

- 泡沬排序法的時間複雜度為 $n^2$，即最差的情況(由大到小排序時)需要 $n * n-1$ 輪才能讓所有數字由小到大排列。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while (cases-- > 0) {
        int number = sc.nextInt();
        int[]arr = new int[number];
        for(int i = 0; i < number; i++) {
            arr[i] = sc.nextInt();
        }

        int results = 0;
        for(int i = 0; i < arr.length - 1; i++) {
            for(int j = 0; j < arr.length - i - 1; j++) {
                int temp = 0;
                if (arr[j] > arr[j+1]) {
                    temp = arr[j+1];
                    arr[j+1] = arr[j];
                    arr[j] = temp;
                    results++;
                }
            }
        }
        System.out.println("Optimal train swapping takes " + results + " swaps.");
    }
  }
};
```

# UVA948：Fibonaccimal Base

 [Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=24&page=show_problem&problem=889)

- 費氏數列： 0 1 1 2 3 5 8 13 21 34 ....，即兩數相加等於第三數，以此類推。

## 題目概要

- 首先輸入共 N 筆資料。
- 找出數值 X 的費氏數列並轉換為二進制，如 X: 17 = **13 + 3 + 1**
  - **13  8  5  3  2  1**
  - 1    0  0  1  0  1
  - 因此 17 = 13 + 3 + 1  = `100101`

## 解題技巧

- 首先建立費氏數列表 (用遞迴寫很簡潔，但效能沒有迴圈來的好，看個人選擇)

- 測資數值不是很大，所以先建個長度為 40 的 array 就行。

- 找到距離 X 最相近的費氏數列索引再慢慢往回推，若 X 比該索引在費氏數列的值還大那就輸出 1，並且將 X 減去該費氏數列值，反之則輸出 0。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    // 獲得費氏數列前四十個的值
    int[] arr = new int[40];
    for (int i = 0; i <= 39; i++) {
        arr[i] = fib(i);
    }

    while (cases-- > 0) {
        int number = sc.nextInt();
        int index = arr.length - 1;

        // 找到距離該數最相近的費氏數列的索引
        while (number < arr[index]) {
            index--;
        }
        System.out.print(number + " = ");
        // 從最相近的索引開始往回找
        for (int j = index; j >= 1; j--) {
            // 若該數比費氏數列的數值大則輸出 1 並減去該費氏數列值
            if (number >= arr[j]) {
                System.out.print('1');
                number -= arr[j];
            } else { // 相反則輸出 0
                System.out.print('0');
            }
        }
        System.out.println(" (fib)");
    }
  }
  // 建立費氏數列
  public static int fib(int n) {
      if(n == 0) return 1;
      else if (n == 1) return 1;
      else return fib(n - 2) + fib(n - 1);
  }
};
```

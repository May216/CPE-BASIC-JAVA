# UVA10931：Parity

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&category=24&problem=1872)

## 題目概要

- 輸入 N 筆測資。

- 將輸入的 X 值轉換為二進位，並計算出轉為二進位時有幾個 1。

## 解題技巧

- 使用 `Integer.toBinaryString` 可以將數字轉為二進位(字串)來處理。

- 使用 `str.charAt()` 搭配 for 迴圈來檢查有幾個 1 。

## 程式碼

```java
import java.util.Scanner;

public class Uva10931 {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);

        int num;
        while(sc.hasNext() && (num=sc.nextInt()) != 0) {
            String str = Integer.toBinaryString(num);
            int count = 0;
            for (int i = 0;i <str.length(); i++) {
                if (str.charAt(i) == '1') count++;
            }

            System.out.println("The parity of " + str + " is " + count + " (mod 2).");
        }
    }
}
```

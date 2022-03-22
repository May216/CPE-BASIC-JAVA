# UVA10162：Last digit

## 題目概要

- 每行都是一筆測資，輸入為 N (1 ≦ N ≦ 2 * $10^100$)，需計算 S = $1^1 + 2^2 + 3^3 + ... + N^N$ 並輸出 S 的最後一位數。

## 解題技巧

- 看著容易實際需要思考一下的題目，因為範圍很大所以不能用 int 和 long 來處理，要用 String 來處理。

- 需要先計算規律，可得知每20個數之後尾數都會比上次循環多 4，100 個數之後又會重頭開始。
  
  - 0，1，5，2，8，3，9，2，8，7，7，8，4，7，3，8，4，1，5，4
  
  - 4，5，9，6，2，7，3，6，2，1，1，2，8，1，7，2，8，5，9，8
  
  - 8，9，3，0，6，1，7，0，6，5，5，6，2，5，1，6，2，9，3，2
  
  - 2，3，7，4，0，5，1，4，0，9，9，0，6，9，5，0，6，3，7，6
  
  - 6，7，1，8，4，9，5，8，4，3，3，4，0，3，9，4，0，7，1，0

- 取出輸入的數字最後的 2 位（即 %100），輸出 ((value % 20 + 4 * value / 20)) % 10  即可。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int maps[] = { 0, 1, 5, 2, 8, 3, 9, 2, 8, 7, 7, 8, 4, 7, 3, 8, 4, 1, 5, 4 };

    while(sc.hasNext()) {
        String str = sc.next();
        if(str.equals("0")) break;
        int len = str.length();
        int value = str.charAt(len - 1) - '0'; // 當前個位數
        if(len > 1) value += (str.charAt(len - 2) - '0') * 10; // 當前十位數
        // maps[value % 20] : 20個數小循環中的哪個數
        // value / 20 * 4 : 找出是位於第幾個小循環, 判斷要加幾個4(每次小循環都比上次多4)
        // 最後 % 10 是為了取個位數 (last digit)
        System.out.println((maps[value % 20] + value / 20 *  4) % 10);
    }
  }
};
```

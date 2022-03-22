# UVA11309：Counting Chaos

## 題目概要

- 第一行輸入一個正整數 N 代表有 N 筆測資，每筆測資皆為 HH:mm 格式的字串，代表當前時間(24小時制)，請計算出下一個迴文時間(不包括當下)。
  
  - 迴文時間：15:51 , 13:31 左至右 右至左讀起來都一樣的時間。

## 解題技巧

- 將時間轉為字串，用 StringBuilder 的 reverse() 來判斷是否和反轉前一樣。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        String time = sc.next();
        int h = (time.charAt(0) - '0') * 10 + (time.charAt(1) - '0');
        int m = (time.charAt(3) - '0') * 10 + (time.charAt(4) - '0');

        while(true) {
            m++;
            h = (m/60 + h) % 24;
            m = m % 60;
            String temp = Integer.toString(h*100 + m); //小時 * 100 + 分 → 23:30 => 2330
            StringBuilder temp2 = new StringBuilder(temp);
            if(temp.equals(temp2.reverse().toString())) break; // 當回文就停止
        }
        System.out.println("" + (h/10) + (h%10) + ":" + (m/10) + (m%10)); // 個位數要補0
    }
  }
};
```

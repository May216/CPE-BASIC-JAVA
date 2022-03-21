# UVA10193：All You Need is Love

## 題目概要

- 判斷一組二進位的測資(S1, S2) 能否不斷被同一個二進位 L 扣除，直到等於 L，如果可以則輸出 `All you need is love!` 否則輸出 `Love is not all you need!`。

## 解題技巧

- 其實就是在求 S1, S2 是否有大於 1 的公因數。

- 先把一組二進位 S1 和 S2 轉為十進位整數，再去求兩數是否有公因數。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    for(int i = 0; i < cases; i++) {
        String str1 = sc.next(), str2 = sc.next();
        // 將二進位轉為十進位整數
        int s1 = Integer.parseInt(str1, 2);
        int s2 = Integer.parseInt(str2, 2);
        // 求公因數
        while(s2 != 0) {
            int temp = s2;
            s2 = s1 % s2;
            s1 = temp;
        }

        if(s1 != 1 && s2 == 0) System.out.println("Pair #" + (i + 1) + ": All you need is love!");
        else System.out.println("Pair #" + (i + 1) + ": Love is not all you need!");
    }
  }
};
```

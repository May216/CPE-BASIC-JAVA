# UVA10190：Divide, But Not Quite Conquer

## 題目概要

- 每行都是一筆測資，每筆測資有 n, m 兩數，判斷 n 是否為 m 的某次方，如果是則依次輸出 n /= m 的結果，如果不是則輸出 Boring!

## 解題技巧

- 無

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        long n = sc.nextLong(), m = sc.nextLong();
        int t = 1;
        while(t < n && m >= 2) t *= m; // 將 t *= m 直到 t 最接近 n 或等於 n
        if(t == n && m >= 2 && n >= m) { // 若 t = n 代表 n 為 m 的倍數
            for(long i = n; i >= 1; i /= m) { // 依次輸出 n /= m 的結果
                System.out.print(i);
                if(i != 1) System.out.print(" ");
            }
            System.out.println("");
        } else System.out.println("Boring!");

    }
  }
};
```

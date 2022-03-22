# UVA10994：Simple Addition

## 題目概要

- 每行都是一筆測資，每筆測資包含兩個整數 q, p，若兩個數皆為負數則終止，請按照題目給定的函式計算出 p ~ q 的總和。

## 解題技巧

- 不能直接根據題目的函式寫成 function + for 迴圈來做，會超時。
- 改成使用 (1 + 2 + 3 + ... + q) - (1 + 2 + 3 + ... + p) 來計算
- 計算出多少個 10 的倍數 (1 + 2 + ... + 9 = 45 所以可以直接個數 * 45) + 剩下的數字 (10 的餘數)

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    long p=0,q=0;
        while(sc.hasNext() && (p=sc.nextLong())>=0 && (q=sc.nextLong())>=0){
            long sum=0;
            p--;
            //計算sum - 1 ~ (p - 1)的總和
            while(p > 0){
                sum = sum - (p / 10) * 45 - (p % 10 + 1) * (p % 10) / 2; 
                p /= 10;
            }

            //計算sum + 1 ~ q 的總和
            while(q > 0){
                sum = sum + (q / 10) * 45 + (q % 10 + 1) * (q % 10) / 2;
                q /= 10;
            }

            //結果輸出
            System.out.println(sum);
        }
  }
};
```

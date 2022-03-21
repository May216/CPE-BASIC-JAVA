# UVA10925：Krakovia

## 題目概要

- 每筆測資第一行會有兩個正整數 N, F，N 為總共的人數，F 為需要支付費用的人數，請計算出總共需要多少錢以及平均每個人要支付的費用為多少。

## 解題技巧

- 唯一需要注意的是 input 有可能超過 int 的範圍，所以用 long 比較保險。

- 每筆測資結果之間都要再空一行。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc=new Scanner(System.in);
    int count = 0;
       while(sc.hasNext()) {
           int N = sc.nextInt(), F = sc.nextInt();
           if (N == 0 && F == 0) break;
           count++;
           long pay[] = new long[N];
           long sum = 0;
           for(int i = 0; i < N; i++) {
               pay[i] = sc.nextLong();
               sum += pay[i];
           }

           System.out.println("Bill #" + count + " costs " + sum + ": each friend should pay " + (sum / F) + "\r\n");
       }
  }
};
```

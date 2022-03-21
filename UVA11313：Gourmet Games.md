# UVA11313：Gourmet Games

## 題目概要

- 第一行輸入一個正整數 N，代表有 N 筆測資，接著每行為一筆測資，每筆測資會有兩個整數 n, m，n 為參賽者人數，m 為每集參與的廚師人數。

- 每個測資要輸出選出一個新廚師所需的節目集數。要是比賽無法以所給的 n 和 m 來完成，印出「cannot do this」。

## 解題技巧

- 總共 n 人，每集需要參與 m 人，且每集會晉級 1 人，所以一輪後會剩下 n - m + 1 人，以此類推直到最後 n 剩下一人。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        int n = sc.nextInt(), m = sc.nextInt();
        int count = 0;
        while(n > 1) {
            n = n - m + 1;
            count++;
        }
        if(n == 1) System.out.println(count);
        else System.out.println("cannot do this");
    }
  }
};
```

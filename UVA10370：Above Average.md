# UVA10370：Above Average

## 題目概要

- 第一行輸入 N 筆測資；

- 每一筆測資開頭第一個數字為這筆測資總共有 C 個學生(1 ≦ C ≦ 1000)；

- 接下來的 C 個數字代表學生的成績(0 ≦ C ≦ 100)；

- 算出 C 位學生的平均分數，並計算出高於平均數的學生比率為多少(算至小數點後三位)。

## 解題技巧

- 這題比較需要注意的是型別之間的轉換，算平均數的時候用浮點數，算有幾個高於平均分數的時候也要轉為浮點數。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
       int cases = sc.nextInt();
       while(cases-- > 0) {
           int n = sc.nextInt();
           int arr[] = new int[n];
           double avg = 0;
           for(int i = 0; i < n; i++) {
               arr[i] = sc.nextInt();
               avg += arr[i];
           }
           avg /= n;
           double counts = 0;
           for(int i: arr) if (i > avg) counts++;
           System.out.printf("%.3f%%\r\n", (counts / n) * 100);
       } 
  }
};
```

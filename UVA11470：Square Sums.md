# UVA11470：Square Sums

## 題目概要

- 測資第一行為正整數 N，代表為 N * N 矩陣，需算出矩陣由外而內每一層相加的結果。
  
  例如：
  
  5 3 2 7 9
  
  1 7 4 2 4
  
  5 3 2 4 6
  
  1 3 4 5 1
  
  1 4 5 6 3
  
  最外圈為 5+3+2+7+9+1+4+5+6+1+1+1+4+5+6+3 = 63
  
  再往內一圈為 7+4+2+3+4+3+5 = 32
  
  最後一圈為 2

- 當 N 為 0 時終止。

## 解題技巧

- 用二維陣列儲存矩陣中的值。

- 計算整個矩陣總和，再往內縮一圈減去內圈總和就可以得到最外層總和，以此類推直到最後一層。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int Case = 1;
       while(sc.hasNextLine()) {
           int n = sc.nextInt();
           if(n == 0) break;
           int arr[][] = new int[n][n];
           for(int i = 0; i < n; i++) {
               for(int j = 0; j < n; j++) {
                   arr[i][j] = sc.nextInt();
               }
           }
           System.out.printf("Case %d:", Case++);
           int s = 0, e = n;
           while(s <= e) {
               int out = 0, in = 0;
               // 外圈總和
               for(int i = s; i < e; i++) {
                   for(int j = s; j < e; j++) {
                       out += arr[i][j];
                   }
               }
               // 內圈總和
               for(int i = s + 1; i < e - 1; i++) {
                   for(int j = s + 1; j < e - 1; j++) {
                       in += arr[i][j];
                   }
               }

               if((out - in) != 0) System.out.print(" " + (out - in));
               s++;
               e--;
           }
           System.out.println("");
       }
  }
};
```

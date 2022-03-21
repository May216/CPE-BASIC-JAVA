# UVA11417：GCD

## 題目概要

- 根據題目給定的公式，算出兩數最大公因數加總。

## 解題技巧

- 用輾轉相除法求最大公因數。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {

        int n = sc.nextInt();
        if (n == 0) break;
        int G = 0;
        for(int i = 1; i < n; i++) {
            for(int j = i + 1; j <= n; j++) {
                G += GCD(i, j);
            }
        }
        System.out.println(G);
    }
  }

  public static int GCD(int m, int n) {
      if (n == 0) return m;
      else return GCD(n, m % n);
  }
}; 
```

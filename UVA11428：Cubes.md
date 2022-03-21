# UVA11428：Cubes

## 題目概要

- 給定一個正整數 N(0≦N≦10000)，求出 N = $x^3 - y^3$ 的 x 與 y 為多少。

## 解題技巧

- 寫兩個迴圈找到 $x^3 - y^3 = N$ 的 x 與 y。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int N = sc.nextInt();
        if(N == 0) break;
        int x = 0, y = 0, flag = 0;
        for(x = 1; x < 60; x++) {
            for(y = 0; y < x; y++) {
                if (Math.pow(x, 3) - Math.pow(y, 3) == N) {
                    flag++;
                    break;
                }
            }
            if (flag == 1) break;
        }
        if(x == 60 || y == 0) System.out.println("No solution");
        else System.out.println(x + " " + y);
    }
  }
};
```

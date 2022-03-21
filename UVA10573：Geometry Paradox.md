# UVA10573：Geometry Paradox

## 題目概要

- 兩個相切的小圓同時外切於一個大圓 R，已知兩個小圓的半徑為 r1, r2、大圓內公切線長度為 t，求大圓面積減去兩小圓面積為多少(灰色區域)。

## 解題技巧

- 需要判斷輸入的是不是兩個整數，如果只有一個整數就是 t 的值，若是兩個值代表是 r1 和 r2 的值。所以我們得用 String.split(" "); 來判斷長度再繼續進行。
- $R = r1 + r2$; $t^2 = 4(R^2 - (r2 - r1) ^2) = 4 * r1 * r2$; 從前面可以得知 $S = PI * (R^2 - r1^2 - r2^2) = PI * r2 * r1 * 2 = PI * t^2 / 8$
- 所以如果是給兩個圓半徑，可以用 $PI * r2 * r1 * 2$，如果給的是 t 就用 $PI * t^2 / 8$ 計算。
- 還有很坑的一點是，不能直接用 `nextInt()` 來抓測資數，因為輸入是字串而不是整數，所以得用 `Integer.parseInt(sc.nextLine())` 來獲取測資數。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = Integer.parseInt(sc.nextLine());
    while(cases-- >0){
        String str[] = sc.nextLine().split(" ");
        double t = 0, r1 = 0, r2 = 0, ans = 0;
        final double PI = Math.PI;
        if(str.length == 2){
            r1 = Double.parseDouble(str[0]);
            r2 = Double.parseDouble(str[1]);
            ans = 2 * r1 * r2 * PI;
        }
        else{
            t = Double.parseDouble(str[0]);
            ans = PI * Math.pow(t, 2) / 8;
        }
        System.out.printf("%.4f\r\n",ans);
    }
  }
};
```

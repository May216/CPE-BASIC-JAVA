# UVA10035：Primary Arithmetic

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=976)

## 題目概要

- 輸入 X, Y 並計算出兩數相加過程中總共會進位多少次。

- 若兩數皆為 0 則離開。

## 解題技巧

- 先從個位數相加，然後每次加完都除以 10。

- 其中一位數有可能會是 0，如果是 0 就沒有相加的必要了，直接輸出 No carry operation.

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class Uva10035 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int x = sc.nextInt(), y = sc.nextInt();
        if (x == 0 && y == 0) break;

        int carry = 0; // 用來判斷當前計算有沒有進位
        int counts = 0; // answer
        while (x != 0 || y != 0) {
            if (x % 10 + y % 10 + carry >= 10) {
                counts++;
                carry = 1;
            } else carry = 0;

            x /= 10;
            y /= 10;
        }

        if (counts == 0) System.out.println("No carry operation.");
        else if (counts == 1) System.out.println("1 carry operation.");
        else System.out.println(counts + " carry operations.");
    }
  }
};
```

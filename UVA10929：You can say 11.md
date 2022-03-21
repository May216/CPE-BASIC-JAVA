# UVA10929：You can say 11

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1870)

## 題目概要

- 每行皆為一筆測資。

- 判斷輸入的數值是否為 11 的倍數。

- 若為 0 則離開。

## 解題技巧

- **奇位數減去偶位數再除以 11**，餘數為 0 即代表它為 11 的倍數。
  
  - 例：`3819024` = 奇: $3+1+0+4 = 8$ , 偶: $8+9+2 = 19$ , $奇 - 偶 = 8 - 19 = -11$ ，`-11 % 11 = 0`，因此 `3819024` 為 11 的倍數。

## 程式碼

```java
import java.util.Scanner;

public class Uva10929 {
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);

        while(sc.hasNext()){
            String str = sc.next();

            if(str.equals("0")) break;

            int odd = 0, even = 0;
            for(int i = 0; i < str.length(); i++){
                if(i % 2 == 0) even += str.charAt(i) - 48;
                else odd += str.charAt(i) - 48;
            }

            if((odd - even) % 11 == 0) System.out.println(str + " is a multiple of 11.");
            else System.out.println(str  +" is not a multiple of 11.");
        }
    }
}
```

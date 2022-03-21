# UVA11000：Bee

## 題目概要

- 第一隻母蜂不會死，母蜂可以生一隻公蜂，公蜂可以生一隻母一隻公，且生完後就會死亡，請計算出 n 年之後公蜂數和總蜜蜂數為多少。

- 每行皆為一筆測資，當 n 為 -1 時終止。

## 解題技巧

-  　　　公　母

- N = 0　0　  1

- N = 1　1　  1

- N = 2　2　  2  => 生完後死掉一隻公蜂, 變成 1 2

- N = 3　4　  3 

- N = 4　7　  5

可看出規律為，公蜂 = 上一代蜜蜂總數，母蜂 = 上一代公蜂數 + 1

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    long n;
    while(sc.hasNextLong() && (n = sc.nextLong()) != -1) {
    	long male = 0, female = 1, maleTemp = 0, femaleTemp = 0;
    	while(n > 0) {
    		femaleTemp = male + 1;
    		maleTemp = female + male;
    		female = femaleTemp;
    		male = maleTemp;
    		
    		n--;
    	}
    	
    	System.out.println(male + " " + (male + female));
    }
  }
};
```

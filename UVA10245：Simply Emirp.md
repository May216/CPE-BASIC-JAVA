# UVA10245：Simply Emirp

## 題目概要

- 判斷數字 N 反轉前後是否皆為質數，是就輸出 N is emirp. 若反轉前是質數但反轉後不是就輸出 N is prime. 都不是則輸出 N is not prime.*(例如 23 是質數反轉 32 不是質數 就輸出 23 is prime., 37 反轉 74 還是質數就輸出 37 is emirp)。

## 解題技巧

- 為了反轉數字所以用 String 來做。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        String str = sc.next();
        String reverse = "";

        // 反轉
        for(int i = str.length() - 1; i >= 0; i--)
            reverse += str.charAt(i);

        // 反轉前後皆為質數
        if (isPrime(Integer.parseInt(str)) && isPrime(Integer.parseInt(reverse)) && !str.equals(reverse)) {
            System.out.println(str + " is emirp.");
        } else if (isPrime(Integer.parseInt(str))) { // 反轉前為質數
            System.out.println(str + " is prime.");
        } else { // 都不是質數
            System.out.println(str + " is not prime.");
        }
    }
  }
  // 判斷是否為質數 (有沒有除了 1 和本身之外的因數)
  public static boolean isPrime(int n) {
      boolean flag = true;
      for(int i = 2; i <= n / 2; i++) {
          if (n % i == 0) {
              flag = false;
              break;
          }
      }
      return flag;
  }
};
```

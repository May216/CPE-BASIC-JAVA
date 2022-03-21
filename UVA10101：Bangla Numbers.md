# UVA10101：Bangla Numbers

## 題目概要

- 換算錢的單位後輸出，類似 304320 = 三十萬四千三百二十元。

## 解題技巧

- 用遞迴的方式來換算單位。calculate 只需要輸出值不需要回傳值，所以用 void。
- 項次前面有空三格，包括項次就是四格，所以要用 `printf("%4d.")` 的方式輸出項次。%4d 代表以 4 位數顯示一個整數，例如 1 會變成 `   1`。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int count = 1;
    while(sc.hasNext()) {
    	System.out.printf("%4d.", count);

    	long num = sc.nextLong();
    	if(num == 0) System.out.printf(" 0");
    	else calculate(num);
    	
    	count++;
    	System.out.println("");
    }
  }
  
  public static void calculate(long n) {
  	if (n >= 10000000) {
  		calculate(n / 10000000);
  		System.out.print(" kuti");
  		n = n % 10000000;
  	}
  	if (n >= 100000) {
  		calculate(n / 100000);
  		System.out.print(" lakh");
  		n = n % 100000;
  	}
  	if (n >= 1000) {
  		calculate(n / 1000);
  		System.out.print(" hajar");
  		n = n % 1000;
  	}
  	if (n >= 100) {
  		calculate(n / 100);
  		System.out.print(" shata");
  		n = n % 100;
  	}
  	if (n > 0) System.out.print(" " + n);
  }
};
```

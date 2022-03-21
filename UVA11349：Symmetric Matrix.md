# UVA11349：Symmetric Matrix

## 題目概要

- 判斷 n * n 的矩陣是否為對稱矩陣。

## 解題技巧

- 判斷 `arr[j] != arr[(n*n) - 1 - j]` 是否相同直至 j = n * n 即可。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    for(int i = 1; i <= cases; i++) {
        System.out.printf("Test #%d: ", i);
        String empty1 = sc.next(), empty2 = sc.next(); // N =
        int n = sc.nextInt();

         int size = n*n;
        long arr[] = new long[size];

        for(int j = 0; j < size; j++) {
            arr[j] = Long.parseLong(sc.next());
        }

        boolean flag = true;
        for(int j = 0; j < size; j++) {
            if(arr[j] < 0 || (arr[j] != arr[size - 1 - j])) {
                flag = false;
                break;
            }
        }

        if (flag) System.out.print("Symmetric.");
        else System.out.print("Non-symmetric.");

        System.out.println("");
    }
  }
};
```

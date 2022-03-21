# UVA11059：Maximum Product

## 題目概要

- 測資第一行為整數 N，代表有 N 個數字，須找出這 N 個數字中連續相乘的最大值。例如 S = {2, 5, -1, 2, -1} , 2  *  5  * -1  * 2  * -1 = 20  

## 解題技巧

- 用迴圈遍歷從左至右一個一個乘找到最大值。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int count = 0;
    while(sc.hasNextInt()) {
        count++;

        int n = sc.nextInt();
        int arr[] = new int[n];
        for(int i = 0; i < n; i++) arr[i] = sc.nextInt();

        long max = 0;
        for(int i = 0; i < n; i++) {
            long temp = 1;
            for(int j = i; j < n; j++) {
                temp *= arr[j];
                if(max < temp) max = temp;
            }
        }

         System.out.printf("Case #%d: The maximum product is %d.\r\n\r\n", count, max);

    }
  }
};
```

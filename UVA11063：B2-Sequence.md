# UVA11063：B2-Sequence

## 題目概要

- 有一個整數序列 1 <= b1 < b2 < b3，將其任兩數相加之和不可重複。
  例如：1, 5, 6, 8 => 1 + 1 , 1 + 5, 1 + 6 , 1 + 8 , 5 + 5 , 5 + 6 , 5 + 8 , 6 + 6, 6 + 8

## 解題技巧

- 用一個大小為 20001 的陣列儲存所有總和結果(任一數字不大於 10000 所以相加不會超過 20000)。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = 1;
    while(sc.hasNext()) {
        int n = sc.nextInt();
        int arr[] = new int[n];
        boolean sum[] = new boolean[20001];
         boolean flag = false; // true: not a B2-Sequence

        int current = 0;
        for(int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
            if (arr[i] <= current || arr[i] < 1) flag = true; // 由小至大，數字不能重複
            current = arr[i];
        }

         if (!flag) {
              // 將相鄰的數字(包括本身)相加，直至最後一個數字，總和不重複
             for(int i = 0; !flag && i < n; i++) {
                 for(int j = i; !flag && j < n; j++) {
                     int add = arr[i] + arr[j];
                     if(!sum[add]) sum[add] = true;
                     else flag = true;
                 }
             }
         }
        if(flag) System.out.printf("Case #%d: It is not a B2-Sequence.\r\n\r\n", cases);
        else System.out.printf("Case #%d: It is a B2-Sequence.\r\n\r\n", cases);
        cases++;
    }
  }
};
```

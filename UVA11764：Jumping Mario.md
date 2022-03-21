# UVA11764：Jumping Mario

## 題目概要

- 你將被給予N個牆壁(由左至右)的高度。瑪莉歐(Mario)目前站在第一個牆壁。他必須跳到相鄰的牆壁直到最後一個。這意味著，他將跳躍 N - 1 次。a high jump 代表瑪莉歐(Mario)跳到一個較高的牆，同樣，a low jump代表瑪莉歐(Mario)跳到一個較矮的牆。請找出 a high jump 和 a low jump 的總數。

- 第一行輸入的是一個整數T（T < 30），表示接下來有T筆測資。每筆測資開始於一個正整數 N（N < 50），表示牆壁的數目。下一行依序為 N 個牆壁的高度(由左至右)。每一個高度是不超過10的非負整數。

## 解題技巧

- 無

## 程式碼

```java
import java.util.Scanner;
public class Uva11764 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    for(int i = 1; i <= cases; i++) {
      int n = sc.nextInt();
      int arr[] = new int[n];
      for(int j = 0; j < n; j++) {
        arr[j] = sc.nextInt();
      }
      int high = 0, low = 0;
      for(int j = 1; j < arr.length; j++) {
        if (arr[j] > arr[j - 1]) high++;
        else if (arr[j] < arr[j - 1]) low++; 
      }

      if (n == 1) System.out.println("Case " + i + ": 0 0");
      else System.out.println("Case " + i + ": " + high + " " + low);
    }
  }
}
```

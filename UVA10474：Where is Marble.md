# UVA10474：Where is Marble?

## 題目概要

- 該題可以有多筆測資(< 65)，每筆測資的第一行會有兩個整數 N, Q，N 是大理石的數量，Q是Meena的查詢數量；
- 當 N = 0 且 Q = 0 時停止；
- 接下來 N 行包含 N 個大理石上寫的數字，這些編號沒有任何規律；
- 接下來的 Q 行將進行 Q 次查詢；
- 所有數字皆 <= 10000，並且不為負數。
- 對於每組測資，輸出測資編號。
- 對於每個查詢，如果在位置 y 上找到第一個編號為 x 的大理石就輸出 `x found at y`，如果沒有編號為 x 的大理石輸出 `x not found`

## 解題技巧

- 首先將 N 個大理石的號碼存進 array 再由小到大排序
- 利用線性搜索尋

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = 0;
    while(sc.hasNext()) {
        cases++;
        int N = sc.nextInt(), Q = sc.nextInt();
        if (N == 0 && Q == 0) break;
        System.out.println("CASE# " + (cases) + ":");

        int arr[] = new int[N];
        for (int i = 0; i < N; i++) {
            arr[i] = sc.nextInt();
        }
        Arrays.sort(arr);

        for(int i = 0; i < Q; i++) {
            int num = sc.nextInt();
            int index = Search(arr, num);
            if(index != -1) System.out.println(num + " found at " + index);
            else System.out.println(num + " not found");
        }
    }
  }

  public static int Search(int []arr, int n) {
      for(int i = 0; i < arr.length; i++) {
          if(arr[i] == n) return i + 1;
      }
      return -1;
  }
};
```

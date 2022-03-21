# UVA10057：A mid-summer night's dream

## 題目概要

- 假設有一組數字為 X1、X2、X3...，需找到一個數 A，使得$( |X1-A| + |X2-A| + |X3-A| + ... + |Xn-A|)$ 為最小。

- 每筆測資第一行為共有共有 X 個數字，接下來 X 行為數字(X1, X2....)。

- 輸出為：`中位數(mid) 有幾個和中位數相同的數字(count) A有多少種可能(p)`

## 解題技巧

- 要能夠讓全部數減去 A 時為最小，就代表 A 是中位數。
  
  - 中位數會根據資料數是奇數個或偶數個而有不同，比如奇數個時中位數只有 1 個，偶位數時有兩個，所以兩種情況都需要考慮。

- 計算可能有多少最小值時，資料為奇數個的話答案為1，資料為偶數個的話答案為 2 個中位數相減加 1。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc=new Scanner(System.in);
    while(sc.hasNext()) {
        int num = sc.nextInt();
        int arr[] = new int[num];
        for(int i = 0; i < num; i++) {
            arr[i] = sc.nextInt();
        }
        Arrays.sort(arr);

        int mid = arr[(arr.length - 1) / 2];
        int mid2 = arr[(arr.length) / 2];

        int count = 0;
        for(int i = 0; i < arr.length; i++){
            if(arr[i] == mid || arr[i] == mid2) count++;
        }

        int p = mid2 - mid + 1;

        System.out.println(mid + " " + count + " " + p);
    }
  }
};
```

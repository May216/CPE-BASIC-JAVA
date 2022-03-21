# UVA10093：An Easy Problem!

## 題目概要

- 題目會給一個 N 進制 (2≦ N ≦ 62) 的數字 R，R 保證能被 (N - 1)整除。求符合題意的最小 N 進制。當 N = 62 時，用來表示 62 進制的字符為 0 ~ 9, A ~ Z(10 ~ 35), a ~ z(36 ~ 61)

## 解題技巧

![](C:\Users\user\Desktop\ASCII.png)

- 用 `toCharArray` 將字串轉為字符串陣列。

- 需要把每筆測資拆成一個個字符，然後將每個位數的值相加，因為進制數一定會比在各個位數還大（比如說 12345，進制一定大於 5），所以我們需要把測資裡面的最大值提取出來，從該值開始計算符合題意的最小 N 進制。

- 題目說，R 一定能被 N - 1 整除，即代表所有位數相加 mod X 為 0，R 就是 X + 1。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextLine()) {
        String str = sc.nextLine();
        char temp[] = str.toCharArray();
        int sum = 0;
        int max = 1;
        for(char item: temp) {
            int R = 0;
            if(item >= '0' && item <= '9') {
                R = item - '0';
            } else if(item >= 'A' && item <= 'Z') {
                R = item - 'A' + 10;
            } else if(item >= 97 && item <= 122) {
                R = item - 'a' + 36;
            }
            sum += R;
            if(R > max) max = R;
        }

        for(int i = max; i <= 62; i++) {
            if(i == 62) {
                System.out.println("such number is impossible!");
                break;
            }
            if(sum % i == 0) {
                System.out.println(i + 1);
                break;
            }
        }
    }
  }
};
```

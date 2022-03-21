## UVA10300：Ecological Premium

## 題目概要

- 有 N 筆測資(< 20)，每筆測資的第一行為有 F 個農夫(0 < F < 20)，接下來的 F 行每行有三個正整數，分別為：農場面積(平方米)、擁有的動物數量、環保指數。
- 請先計算出每個動物平均需佔的面積(平方米)，然後將該值乘以環保指數，就能得出每隻動物的支出，將支出乘以動物數量就是答案。
- 每筆測資一個輸出結果，結果為整數。

## 解題技巧

- 面積 / 動物數量 * 環保指數 * 動物數量 `budget = ((area / animals) * env) * animals)` = 面積 * 環保指數 `budget = area * env`
- **資料大小會超過 int，所以請使用 long。**

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        int n = sc.nextInt();
        long budget = 0;
        for(int i = 0; i < n; i++) {
            long area = sc.nextLong(), animals = sc.nextLong(), env = sc.nextLong();
            budget += area * env;
        }
        System.out.println(budget);
    }
  }
};
```

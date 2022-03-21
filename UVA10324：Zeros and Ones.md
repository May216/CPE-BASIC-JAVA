# UVA10324：Zeros and Ones

## 題目概要

- 給定 n 筆 case，每筆 case 的第一行為字串 str，第二行為有 k 個數字組要判斷，每個數自組有兩個數 i, j。

- i, j 是一個範圍，範圍需調整從由小到大，判斷 str 從索引 i ~ j 的數字是否一樣。

## 解題技巧

- 判斷字串在這裡索引範圍內的值是否相容，比如說 str = `0000011111`
  ，總共 3 組，第一組：`0 5` 代表索引 0 ~ 5 的值是否相容, 0 0 0 0 0 1 , 很明顯不相容所以輸入 No，第二組：`4 2`，改成由小到大 `2 4`，索引 2 ~ 4 為 0 0 0，一樣所以輸出 Yes。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int count = 0;
    while(sc.hasNext()) {
        count++;
        System.out.println("Case " + count + ":");

        String str = sc.next();
        int n = sc.nextInt();

        while(n-- > 0) {
            int i = sc.nextInt();
            int j = sc.nextInt();
            int max = 0, min = 0;

            if (i > j) {
                max = i;
                min = j;
            } else {
                max = j;
                min = i;
            }

            Boolean flag = true;
            for(int k = min; k < max; k++) {
                if (str.charAt(k) != str.charAt(k+1)) {
                    flag = false;
                    break;
                }
            }

            if(flag) System.out.println("Yes");
            else System.out.println("No");
        }
    }
  }
};
```

# UVA10050：Hartals

## 題目概要

- 輸入 N 筆測資，接著輸入該筆測資總共的議期天數 Y ，再輸入 X 個政黨以及這 X 個政黨每隔 Z 天休一次，計算出在這段議期間總共休息的天數。

- 週六及週日一定放假。

## 解題技巧

- 要注意同一天不要重複計算，用一個 flag 來判斷就好。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt(); //資料筆數
    while(cases-- > 0){
        int day = sc.nextInt(); //議期
        int parties[] = new int[sc.nextInt()]; //政黨數
        for(int i = 0;i < parties.length; i++){
            parties[i] = sc.nextInt(); //政黨隔幾天休息一次
        }
        int flag = 0;
        int ans = 0;
        for(int i = 1; i <= day; i++) {
            for(int j = 0; j < parties.length; j++) {
                if(i % parties[j] == 0) {
                    flag++;
                    if(!(i % 7 == 6 || i % 7 == 0) && (flag == 1)) ans++;
                }
            }
            flag = 0;
        }
        System.out.println(ans);
    }
  }
};
```

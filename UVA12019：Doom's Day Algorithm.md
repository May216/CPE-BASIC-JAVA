# UVA12019：Doom's Day Algorithm

- [Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=242&page=show_problem&problem=3170)[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=242&page=show_problem&problem=3170)

## 題目概要

- 首先輸入共 N 筆資料。

- 分別輸入 M, D 代表月份和日期。

- 計算2011年M月D日是星期幾。

## 解題技巧

- 2011年 1 月 1 號是禮拜六。

- 將 1 月 1 號到 M 月 D 日總共經過多少天計算出來，最後餘 7 就能得出當天是星期幾。

- 如果以週一作為一週的開始，1 月 1 日就是 `1 % 7 = 1` 會對應到 week[1] = Tuesday，但實際上 2011/01/01 為星期六，所以要向後四個索引 week[5] = Saturday，因此我們會需要將輸入的日期加上 `4`。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();

    while (cases-- > 0) {
        int [] days = {31,28,31,30,31,30,31,31,30,31,30,31};
        String [] week = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};

        int month = sc.nextInt();
        int day = sc.nextInt();
        day = day + 4;

        if (month > 12 || month < 1) return;

        for (int j = 1; j < month; j++) {
            day += days[j - 1];
        }

        System.out.println(week[day % 7]);
    }
  }
};
```

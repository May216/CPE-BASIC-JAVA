# UVA10424：Love Calculator

## 題目概要

- 給你 X 跟 Y 的英文名字，將它依據 a ~ z 的順序(1 ~ 26) 計算名稱總和，比如說 Andy = 1 + 14 + 4 + 25 = 44。

- 當最後總和不是個位數時就繼續相加，變成 4 + 4 = 8；

- 再跟第二個人的名字總和比較，假設第二個人的名字最後總和為 5， 8 > 5 所以 8 作為分母，計算出 $5 / 8$ 取到小數第二位的 % 數為多少。 

- 最大的百分比不能超過 100.00 %。

## 解題技巧

- 因為小寫跟大寫沒有區別，所以可以一律先轉換為大寫或者小寫。

- 用 ASCII code 去計算名字的總和，如果是轉成大寫減去大寫字母的 ASCII code + 1 就能獲得字母的數字，反之亦然。

- 因為結果要到小數點後第二位數，所以就用 float 或者 double 運算都可以。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        // first
        String str1 = sc.nextLine();
        str1 = str1.toUpperCase();
        int sum1 = getSum(str1);
        while (sum1 >= 10) sum1 = calculate(sum1);
        // second
         String str2 = sc.nextLine();
        str2 = str2.toUpperCase();
         int sum2 = getSum(str2);
        while (sum2 >= 10) sum2 = calculate(sum2);

         double ans = ((sum2 > sum1) ? ((double)sum1 / (double)sum2) : ((double)sum2 / (double)sum1)) * 100;
        System.out.printf("%.2f %%\r\n", ans);
    }
  }

  public static int getSum(String n) {
      int sum = 0;
      for (int i = 0; i < n.length(); i++) {
        if (n.charAt(i) >= 'A' && n.charAt(i) <= 'Z') {
            sum += (n.charAt(i) - 'A' + 1);
        }
    }
    return sum;
  }

  public static int calculate(int n) {
      int sum = 0;
      while(n >= 10) {
          sum += n % 10;
          n /= 10;
      }
      return sum + n;
  }
};
```

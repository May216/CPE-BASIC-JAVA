# UVA11461：Square Numbers

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=24&page=show_problem&problem=2456)

## 題目概要

- 輸入 X, Y 並計算出 X ~ Y 之間總共會有幾個完美平方數。

- 完美平方數如：1、4、9、81...

## 解題技巧

- X 或 Y 等於 0 時直接離開。

- 若要檢驗該數是否為完美平方數需要開根號，開根號後有小數就代表不是完美平方數。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc=new Scanner(System.in);
    int x = 0;
    int y = 0;
    while((x = sc.nextInt()) != 0 && (y = sc.nextInt()) != 0){
        int results = 0;
        for (int i = x; i <= y; i++) {
            double num = (int)Math.sqrt(i); // sqrt 開根號出來的型態為 double
            if (i % num == 0) results++;
        }

        System.out.println(results);
    }
  }
};
```

# UVA10055：Hashmat the brave warrior

## 題目概要

- 算出士兵跟敵對士兵相差多少。

## 解題技巧

- 範圍超過 int，所以要用 long。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextLong()) {
        long x = sc.nextLong(), y = sc.nextLong();
        System.out.println(Math.abs(x - y));
    }
  }
};
```

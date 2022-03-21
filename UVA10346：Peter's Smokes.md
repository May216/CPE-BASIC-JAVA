# UVA10346：Peter's Smokes

## 題目概要

- Peter 有 n 根菸，k 個菸頭可以再換一支菸，問 Peter 最多能抽幾支菸。

## 解題技巧

- 只要 n 大於 k 就一直讓總數加上 n / k，並將剩下及兌換後的菸根數相加繼續計算下去。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int n = sc.nextInt();
        int k = sc.nextInt();
        int count = n;
        while (n >= k) {
            count += n / k;
            n = n / k + n % k;
        }
        System.out.println(count);
    }
  }
};
```

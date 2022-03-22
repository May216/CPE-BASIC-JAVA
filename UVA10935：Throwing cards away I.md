# UVA10935：Throwing cards away I

## 題目概要

- 給定一組牌，將第一張丟掉，第二張放到最後，一直重複這個動作直到手中剩下一張牌。
- 每行都是一筆測資，每筆測資有一個正整數 N，代表手裡有 1 ~ N 的牌，輸入 0 終止。
- 輸出最後一張牌以及丟掉的牌。

## 解題技巧

- 用 ArrayDeque 來做，ArrayDeque 允許從兩側添加或刪除元素，可用作堆棧(先進先出) 或 隊列(先進先出)。
- Queue poll() 用於返回並移除容器第一個元素。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    String s = "";
    while(sc.hasNext()) {
        s = "";
        int n = sc.nextInt();
        if (n == 0) break;
        Queue<Integer> q = new ArrayDeque<Integer>();

        for(int i = 1; i <= n; i++) q.add(i);

        while(!q.isEmpty()) {
            if (q.size() == 1) break;
            String k = "" + q.poll();
            q.add(q.poll());
            s += k + (q.size() > 1 ? ", " : "");
        }
        System.out.println("Discarded cards: " + s);
        System.out.println("Remaining card: " + q.poll());
    }
  }
};
```

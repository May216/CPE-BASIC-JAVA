# UVA10409：Die Game

## 題目概要

- 請算出翻轉完畢後由上往下看的骰子點數。
- 有 N 個測資，每筆測資的第一行為一個整數，代表骰子會經過幾次翻轉。
- 當朝北邊轉時，本來朝南的一面會變成朝上，本來朝上的一面會變成朝北，本來朝北的一面會朝下...以此類推。

## 解題技巧

- 對應面的骰子數值相加為 7，因此 1 對面就會是 6。而 1 最開始時朝正上方，所以能得知最下方為 6，以此類推找出開始時的東南西北數值。
- 骰子往南或者北轉只會影響南北數字，往東或往西轉只會影響往西數字。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int n = sc.nextInt();
        if (n == 0) break;
        int now = 1;
        int N = 2, W = 3, S = 5, E = 4;
        for (int i = 0; i < n; i++) {
            String direction = sc.next();
            if(direction.equals("north")) {
                N = now;
                now = S;
                S = 7 - N;
            }
            else if(direction.equals("south")) {
                S = now;
                now = N;
                N = 7 - S;
            }
            else if(direction.equals("east")) {
                E = now;
                now = W;
                W = 7 - E;
            }
            else if(direction.equals("west")) {
                W = now;
                now = E;
                E = 7 - W;
            }
        }
        System.out.println(now);
    }
  }
};
```

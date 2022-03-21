# UVA11001：Necklace

## 題目概要

- 有 Vtotal 體積的材料分成 n 份，做成 n 個相同的盤子，總半徑為 n * sqrt(Vtotal/n - V0)。V0 是一個給定的限制，Vtotal/n < V0 時輸出 0，請計算出總半徑最大的 n 值，以便製作出最長的項鍊。

- 如果這個數字不是唯一的，或者根本無法形成項鍊，則輸出“0”。

## 解題技巧

- 配方法求最大值，n = Vtotal / (2 * V0)

- 解不唯一時：n 的小數部分是 0.5

- 無解時情況：Vtotal <= V0

- Vtotal <= 2 * V0 時結果為 1

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextLine()) {
    	int v = sc.nextInt(), v0 = sc.nextInt();
    	if(v == 0 && v0 == 0) break;
    	if (v <= v0) System.out.println('0');
    	else if (v <= 2 * v0) System.out.println('1');
    	else {
    		if ((0.5 * v / v0) - (int)(0.5 * v / v0) == 0.5) {
    			System.out.println("0");
    		} else if ((0.5 * v / v0) - (int)(0.5 * v / v0) < 0.5) {
    			System.out.printf("%d\r\n", (int)(0.5 * v / v0));
    		} else {
    			System.out.printf("%d\r\n", (int)(0.5 * v / v0) + 1);
    		}
    	}
    }
  }
};
```



# UVA11689：Soda Surpler

## 題目概要

- 類似可樂(UVA11150)和買菸題(UVA10346)，每組測試資料1列，含有 3 個整數  e,f,c 。e（0 <=  e < 1000）代表Tim一開始擁有的空瓶子數目，f（0 <=  f < 1000）代表Tim在這一天他在街上收集到的空瓶子數目，c（1 <  c < 2000）代表多少個空瓶子可以換一瓶新的汽水。

- 對每一組測試資料輸出一列，代表 Tim 可以喝到多少瓶汽水。

## 解題技巧

- 無

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
    	// e: 手裡有的空瓶, f: 路上撿的空瓶, c: 幾瓶可以換汽水
    	int e = sc.nextInt(), f = sc.nextInt(), c = sc.nextInt();
    	// 手裡有的空瓶數
    	int now = e + f;
    	// 兌換的空瓶數
    	int count = 0;
    	while((now / c) != 0) {
    		// 手裡空瓶數 / c = 可以換幾瓶汽水
    		count += now / c;
    		// 手裡的空瓶 = 換了幾瓶汽水 + 剩下的汽水
    		now = now / c + now % c;
    	}
    	System.out.println(count);
    }
  }
};
```

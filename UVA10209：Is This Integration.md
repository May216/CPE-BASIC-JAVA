# UVA10209：Is This Integration?

## 題目概要

- 每行是一筆測資，每筆測資有一個浮點數，為正方形的邊長 a，且以正方形每個角為圓心作圓（半徑為ａ）。需分別算出格子、條紋和點點區塊的面積。

- 按照斜線, 點點, 格子順序輸出。

## 解題技巧

![擷取.PNG](https://pic.pimg.tw/a7069810/1474948098-2159512261.png)

- 格子面積：正方形(ABCD) - 2 * 1/12圓(AED、BCE) - 正三角形(ABE)。
  
  點點面積：正方形(ABCD) - 1/4圓(ABD) - 2 * 格子面積。
  
  斜線面積：正方形(ABCD) - 4 * 個子面積 - 4 點點面積。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
    	double a = sc.nextDouble();
    	double square = Math.pow(a, 2);
    	// 格子
    	double x = square - (square * Math.PI / 6) - (square * Math.sqrt(3) / 4);
    	// 點
    	double y = square - (square * Math.PI / 4) - 2 * x;
    	// 斜線
    	double z = square - 4 * x - 4 * y;
    	// 斜線, 點, 格子
    	System.out.printf("%.3f %.3f %.3f", z, 4 * y, 4 * x);
    	System.out.println("");
    }
  }
};
```



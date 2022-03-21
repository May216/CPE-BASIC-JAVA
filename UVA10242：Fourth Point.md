# UVA10242：Fourth Point

## 題目概要

- 給定平行四邊形的兩個相鄰邊 x, y 座標，找出第四個點的 x, y 座標

- 每行為一筆測資，每筆測資會有八個浮點數，每兩個浮點數為一組座標。

## 解題技巧

- 無

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextDouble()) {
    	double[] px = new double[4];
    	double[] py = new double[4];
    	double x = 0, y = 0;
    	for(int i = 0; i < 4; i++) {
    		px[i] = sc.nextDouble();
    		py[i] = sc.nextDouble();
    		x += px[i];
    		y += py[i];
    	}
    	
    	for(int i = 0; i < 4; i++) {
    		for(int j = i + 1; j < 4; j++) {
    			if(px[i] == px[j] && py[i] == py[j]) {
    				System.out.printf("%.3f %.3f\r\n", x - px[i] * 3, y - py[i] * 3);
    				break;
    			}
    		}
    	}
    }
  }
};
```

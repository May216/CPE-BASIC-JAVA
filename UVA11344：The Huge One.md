# UVA11344：The Huge One

## 題目概要

- 輸入第一行包含數字N (0 < N ≤ 2000)，代表有幾組測資。每組測資的第一行包含數字M (0 ≤ M ≤ 10^1000)。  第二行包含集合S中的元素數量，以及集合中的數字。 第二行的數字皆由空格分隔。集合S元素皆在[1~12]的範圍內。

- 對於每組測資輸出一行：  如果數字M可被集合S中的所有數字整除輸出"M - Wonderful."  否則輸出"M - Simple."。

## 解題技巧

- 因為被除數很大，可以考慮用字串或者 BigInteger來處理，再用個 Vector 來存放除數。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
import java.math.BigInteger;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int N = sc.nextInt();
    while(N-- > 0) {
    	BigInteger M = sc.nextBigInteger(); // 被除數
    	int S = sc.nextInt(); // 除數個數
    	Vector<BigInteger> vector = new Vector<BigInteger>(); // 除數
    	for(int i = 0; i < S; i++) {
    		vector.add(sc.nextBigInteger());
    	}
    	
    	boolean flag = true;
    	Iterator<BigInteger> itr = vector.iterator();
    	while(itr.hasNext()) {
    		BigInteger d = itr.next();
    		if (M.mod(d) != BigInteger.ZERO) {
    			flag = false;
    		}
    	}
    	if (flag) System.out.println(M + " - Wonderful.");
    	else System.out.println(M + " - Simple.");
    }
  }
};
```



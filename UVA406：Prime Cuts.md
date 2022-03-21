# UVA406：Prime Cuts

## 題目概要

- 每行都是一筆測資，每筆測資有兩個整數 N、C，N 代表需要 1 ~ N 中的所有質數，C 代表從中心向左右延伸出 C 個質數，當擁有偶數個質數時則印出 2C 個質數；當有奇數個質數時則印出 2C - 1個質數。

- 1 ≦ N ≦ 1000；1 ≦ C ≦ N

## 解題技巧

- 用 ArrayList 來解。

- 首先建立 1 ~ 1000 的質數表，接著計算出 1 ~ N 總共多少個質數，再判斷質數個數為偶數還是奇數做相應的計算。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    ArrayList<Integer> list = new ArrayList<>();
    // 建立 1 ~ 1000 內的質數表
    for(int i = 1; i <= 1000; i++) {
        list.add(i);
        for(int j = 2; j < i; j++) {
            if (i % j == 0) {
                list.remove(new Integer(i));
                break;
            }
        }
    }
    while(sc.hasNext()) {
        // n: 需要 1 ~ N 中的所有質數
        // c: 從中心向左右延伸出 C 個質數
        // size: 1 ~ N 總共有多少個質數
        int n = sc.nextInt(), c = sc.nextInt(), size = 0; 
        for(int i: list) {
            if (i <= n) size++;
            else break;
        }
        System.out.print(n + " " + c + ":");

        /*輸出資料:
          1. 題目要求輸出 C*2 or C*2-1 (個)從中間向左右延伸的質數。
          2. (總質數個數 - 需輸出的質數個數) = 剩下頭尾不輸出的部分。
          3. 由上面的式子/2=印出質數開始點。總質數個數-(上面式子/2)=印出質數的結束點。
        */
        int s = 0;
        if(size % 2 == 0){
            if((c * 2) < size) s = (size - c * 2) / 2; 
            for(int i = s; i < size - s; i++){
                System.out.print(" " + list.get(i));
            }
        }else{
            if((c * 2 - 1) < size) s = (size - (c * 2 - 1)) / 2;
            for(int i = s; i < size - s; i++){
                System.out.print(" " + list.get(i));
            }
        }

        System.out.println("\r\n");
    }
  }
};
```

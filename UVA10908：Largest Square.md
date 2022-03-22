# UVA10908：Largest Square

## 題目概要

- 根據給定的 M * N 矩形，找出以 X, Y 為中心向外延展出的最大正方形邊長(延展的每個點要和中心點是相容字元)。

- 輸入的 N 筆測資，每筆測資開頭為 M, N, Q，M 為列 N 為行，Q 為要檢測的中心點有幾筆，這 Q 列每列都會有兩個整數 X, Y，即為以 M*N 中的 X, Y 那個點向外延展。

## 解題技巧

- 用二維陣列來存 M * N 的值。

- 用 x-i ~ x+i 和 y-i ~ y+i 可以在中心向外延展出九宮格，需考慮出界的情況。

- 因為是從中心向外延展，所以一定會是正方形，邊長會以 i*2-1 的倍率增長。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        int M = sc.nextInt(), N = sc.nextInt(), Q = sc.nextInt();
        char map[][]=new char[M][N];
        for(int i = 0 ;i < M; i++){
            String temp = sc.next();
            for(int j = 0; j < N; j++){
                map[i][j] = temp.charAt(j);
            }
        }
        System.out.println(M + " " + N + " " + Q);
        while(Q-- > 0) {
            int x = sc.nextInt(), y = sc.nextInt();
            char center = map[x][y];
            int i;
            for(i = 0; i < M; i++) {
                boolean flag = true;
                for(int j = x - i; j <= x + i && flag; j++) {
                    for(int k = y - i; k <= y + i; k++) {
                        if(j < 0 || k < 0 || j >= M || k >= N || center != map[j][k]) {
                            flag = false;
                            break;
                        }
                    }    
                }
                if(!flag) break;
            }
            System.out.println(i * 2 - 1);
        }
    }
  }
};
```

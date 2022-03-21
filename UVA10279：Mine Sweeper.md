# UVA10279：Mine Sweeper

## 題目概要

- 第一行輸入 N 筆測資，再來輸入一個≦10的正整數 X 表示有 X * X 的地圖（.表示未踩過 *表示已經踩過），接著又會有 X * X 的矩陣表示即將要踩的點，我們需要計算踩的點周圍的炸彈數量（沒踩的地方用 . 表示，踩到地雷用 * 表示，否則顯示周圍炸彈數量）。

## 解題技巧

- 一直迴圈一直迴圈一直迴圈...炸彈周圍九宮格都 +1。

- 格式要求很刁鑽，每筆測資之間要留一行空白，每筆測資最後一列結果不用空格換行。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();

    for(int counts = 0; counts < cases; counts++) {
        if(counts != 0) System.out.println();
        int x = sc.nextInt();
        // 地圖
        char arr[][] = new char[x][x];
        for(int i = 0; i < x; i++) {
            String str = sc.next();
            for(int j = 0; j < x; j++) {
                arr[i][j] = str.charAt(j);
            }
        }
        // 踩的點
        char arr2[][] = new char[x][x];
        for(int i = 0; i < x; i++) {
            String str = sc.next();
            for(int j = 0; j < x; j++) {
                arr2[i][j] = str.charAt(j);
            }
        }
        // 計算炸彈
        int direction[][]={{0,1},{0,-1},{1,0},{-1,0},{1,1},{-1,-1},{-1,1},{1,-1}};
        int bomb[][] = new int[x][x];
        for(int i = 0; i < x; i++) {
            for(int j = 0; j < x; j++) {
                int count = 0;
                for(int k = 0; k < direction.length; k++) {
                    int row = i + direction[k][0], col = j + direction[k][1];
                    if(row >= 0 && row < x && col >= 0 && col < x && arr[row][col] == '*') count++;
                }
                bomb[i][j] = count;
            }
        }

        // 判斷有沒有踩到炸彈
        boolean flag = true;
        for(int i = 0; i < x; i++) {
            for(int j = 0; j < x; j++) {
                if(arr2[i][j] == 'x') {
                    if(arr[i][j] == '*') {
                        flag = false;
                    }
                }
            }
        }

        for(int i = 0; i < x; i++) {
            for(int j = 0; j < x; j++) {
                if(arr2[i][j] == 'x' && arr[i][j] != '*') System.out.print(bomb[i][j]);
                else if (!flag && arr[i][j] == '*') System.out.print("*");
                else System.out.print(".");
            }
            if(i != (x - 1)) System.out.println("");
        }
      }
  }
};
```

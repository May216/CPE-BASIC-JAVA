# UVA10310：Dog and Gopher

## 題目概要

- 每筆測資第一個數字為總共有 N 個洞，接下來的四個浮點數分別為：地鼠的 X 座標、地鼠的 Y 座標、狗的 X 座標、狗的 Y 座標，接下來的 N 行即為每個洞的  X, Y 座標；

- 狗的速度為地鼠的兩倍，只要地鼠能夠躲進洞裡即代表逃離成功，請計算距離回答地鼠是否會被狗吃掉，如果能夠逃脫需要把逃脫的那個地洞座標輸出。

## 解題技巧

- 要求兩點最短距離，$C^2 = sqrt(a^2 + b^2)$，因為狗的速度為地鼠的兩倍，所以還需要將地鼠的距離 * 2，如果比狗的距離小就代表能脫離成功。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()){
        int num = sc.nextInt();
        double mouseX, mouseY, dogX, dogY, holeX, holeY, successX = 0, successY = 0;
        boolean escape = false;

        mouseX = sc.nextDouble();
        mouseY = sc.nextDouble();
        dogX = sc.nextDouble();
        dogY = sc.nextDouble();

        while(num-- >0){
            holeX = sc.nextDouble();
            holeY = sc.nextDouble();

            double mLength = Math.sqrt(Math.pow(mouseX - holeX, 2) + Math.pow(mouseY - holeY, 2))*2;
            double dLength = Math.sqrt(Math.pow(dogX - holeX, 2) + Math.pow(dogY - holeY, 2));

            if(mLength < dLength){
                escape = true;
                successX = holeX;
                successY = holeY;
            }

        }

        if(escape) System.out.printf("The gopher can escape through the hole at (%.3f,%.3f).\r\n", successX, successY);
        else System.out.println("The gopher cannot escape.");
    }
  }
};
```

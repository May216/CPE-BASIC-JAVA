# UVA12503：Robot Instructions

## 題目概要

- 第一行輸入 N 筆測資，每筆測資的第一行為一個正整數 N，代表有幾行指令，根據指令移動機器人的座標。如果輸入 RIGHT 代表座標 +1；LEFT 為座標 -1；SAME AS X 代表去找第 X 次的指令。

## 解題技巧

- 用 Vector 來保存指令紀錄，方便 SAME AS 查找。

- 因為指令為 1 ~ 100，所以 SAME AS 有可能到十位數或百位數，記得要找完所有數字。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc=new Scanner(System.in);
    int cases = Integer.parseInt(sc.nextLine());
    while(cases-- > 0){
        Vector<String> vector = new Vector<String>();
        int n = Integer.parseInt(sc.nextLine()); // how many commands
        int cur = 0; // current position

        for(int i = 0; i < n; i++){
            String str = sc.nextLine();
            if(str.equals("RIGHT")){
                vector.add("RIGHT");
                cur++;
            }else if(str.equals("LEFT")){
                vector.add("LEFT");
                cur--;
            }else{
                int num = 0;
                for(int j = 0;j < str.length(); j++)
                    if(str.charAt(j) >= '0' && str.charAt(j) <= '9')
                        num = num * 10 + str.charAt(j) - '0';
                if(vector.get(num - 1).equals("RIGHT")){
                    vector.add("RIGHT");
                    cur++;
                }else{
                    vector.add("LEFT");
                    cur--;
                }
            }
        }

        System.out.println(cur);
    }
  }
};
```

# UVA10170：The Hotel with Infinite Rooms

## 題目概要

- HaluaRuti市有一家奇怪的酒店，房間無限。  
  來這家酒店的團體，請遵循以下規則：  
  
  - a）同時，只有能有一個旅行團可以租用酒店。  
  
  - b）每個旅行團在入住日的早晨到達，並在退房日的晚上離開酒店。  
  
  - c）後入住的旅行團需要在前一團退房後的隔天早晨，才能入住  
  
  - d）除了第一團，其他旅行團人數都比前一團多一人  
  
  - e）有n名成員的旅行團則會在酒店停留n天。

- 每行都是一筆測資，輸入兩數 S (1 ≤ S ≤ 10000) 和 D (1 ≤ D < 10^15)，S表示第一組旅行團人數，D表示必須在第D天(從1開始)查找入住酒店的旅行團人數。

## 解題技巧

- S + (S + 1) + (S + 2) + (S + 3) .... + (S + N) >= D，輸出 N

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        long S = sc.nextLong(), D = sc.nextLong();
        long sum = S;
        long count = S;
        while(sum < D) {
            count++;
            sum += count;
        }
        System.out.println(count);
    }
  }
};
```

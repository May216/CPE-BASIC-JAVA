# UVA10281：Average Speed

## 題目概要

- 每行代表的是目前時間(currentTime)和目前速度(currentSpeed)，如果只有時間代表速度和前面一樣沒改變，請計算出目前所經過的距離(distance)，單位為 km/h。

## 解題技巧

- 用 hasNextLine 判斷還有沒有下一筆資料。

- 因為題目給定的速度是 km/h，所以我們要先將時間轉換成毫秒，再將當前時間跟上次紀錄的時間相減後乘上速度就會是距離，由於我們計算前轉換過單位，所以最後要再除 3600 轉換回 km/h。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    double distance = 0, currentSpeed = 0, currentTime = 0, lastTime = 0;
    while(sc.hasNextLine()) {
        int i = 0;
        // 分開時間與速度
        String str[] = sc.nextLine().split(" ");
        while(str[i].equals("")) i++;
        String[] date = str[i].split(":");
        currentTime = Double.parseDouble(date[0])*3600 + Double.parseDouble(date[1])*60 + Double.parseDouble(date[2])*1;
        // 距離 = 時間 * 速度
        distance += (currentTime - lastTime) * currentSpeed / 3600;
        lastTime = currentTime;
        // 判斷有沒有速度, 沒有就輸出
        if(str.length == 1) {
            System.out.printf("%s %.2f km", str[0], distance);
            System.out.println("");
        } else {
            currentSpeed = Double.parseDouble(str[i + 1]);
        }
    }
  }
};
```

# UVA10062：Tell me the frequencies

## 題目概要

- 輸入一行字串，轉換成 ASCII，最後統計出使用到的字符 ASCII 頻率，由小到大輸出，如果有相同頻率的，則優先輸出 ASCII 較大的字符﹒

## 解題技巧

- 無

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = 0;
    while(sc.hasNextLine()) {
        if((cases++) != 0) System.out.println("");
        String str = sc.nextLine();
        int arr[] = new int[127];
        for(int i = 0; i < str.length(); i++) arr[str.charAt(i)]++;

        int max = 0;
        for(int i = 0; i < arr.length; i++) if(arr[i] > max) max = arr[i];

          for(int i = 1; i <= max; i++) {
              for(int j = arr.length - 1; j >= 0; j--) {
                if(arr[j] == i) System.out.println(j + " " + arr[j]);
            }
          }
    }
  }
};
```

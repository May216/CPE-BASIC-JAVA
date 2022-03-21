# UVA10082：WERTYU

## 題目概要

- 將 input 的字串內容根據鍵盤位置往左一個輸出。

- 題目的 O S, GOMR YPFSU/，每個字在鍵盤上往左一格後輸出結果就會是：I AM FINE TODAY.

## 解題技巧

- 英文字母全部使用大寫，在建立鍵盤 string 的時候記得 `\` 要再加上一個 `\` 作為轉譯字符，不然無法識別 \。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNextLine()) {
        String str = sc.nextLine();
        String keyboard = "`1234567890-=QWERTYUIOP[]\\ASDFGHJKL;'ZXCVBNM,./";
        for(int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == ' ') System.out.print(" ");
            for(int j = 0; j < keyboard.length(); j++) {
                if (keyboard.charAt(j) == str.charAt(i)) {
                    System.out.print(keyboard.charAt(j - 1));
                    break;
                }
            }
        }
        System.out.println("");
    }
  }
};
```

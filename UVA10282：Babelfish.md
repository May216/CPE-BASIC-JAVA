# UVA10282：Babelfish

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1223)

## 題目概要

- 查字典。

- 給定 N 筆單字，左邊為英文，右邊為翻譯成不知名語言後的結果，請根據翻譯後的單字將它依據字典翻譯回英文，如果字典中沒有，就輸出 eh。

## 解題技巧

- 用 Map 的 key value 形式來存單字的未知語言和英文。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    Map<String, String> map = new HashMap<String, String>();
    while(true) {
        String str = sc.nextLine();
        if(str.equals("")) break;
        String [] temp = str.split(" ");
        map.put(temp[1], temp[0]);
    }
    while(sc.hasNext()) {
        String str = sc.next();
        if (map.get(str) != null) System.out.println(map.get(str));
        else System.out.println("eh");
    }
  }
};
```

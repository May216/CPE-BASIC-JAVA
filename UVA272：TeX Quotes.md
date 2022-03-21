# UVA272：TeX Quotes

## 題目概要

- 將字串中的雙引號替換掉，如果是第奇數個雙引號就換成 `''` 如果是第偶數個就換成 ````，

## 解題技巧

- 無

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int count = 1;
    while(sc.hasNextLine()) {
        String str = sc.nextLine();
        for(int i = 0; i < str.length(); i++) {
            if (str.charAt(i) == '"') {
                if (count % 2 != 0) System.out.print("``");
                else System.out.print("''");
                count++;
            }
            else System.out.print(str.charAt(i));
        }
        System.out.println("");
    }
  }
};
```

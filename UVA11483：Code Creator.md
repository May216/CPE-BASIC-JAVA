# UVA11483：Code Creator

## 題目概要

- 將字串內容轉為 C++ code 輸出。

## 解題技巧

- 注意 `\` 與 `"` 的轉譯，用 StringBuilder 來做會比較方便。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int n = 0, Case = 0;
    while((n = Integer.parseInt(sc.nextLine().trim())) != 0) {
    	StringBuilder str = new StringBuilder();
    	System.out.printf("Case %d:\r\n", ++Case);
    	str.append("#include<string.h>\r\n#include<stdio.h>\r\nint main()\r\n{\r\n");
    	while(n-- > 0) {
    		char text[] = sc.nextLine().toCharArray();
    		str.append("printf(\"");
    
    		for(char c: text) {
				if(c == '"') str.append("\\\"");
				else str.append(c);
			}
    		str.append("\\n\");\r\n");
    	}
    	str.append("printf(\"\\n\");\r\nreturn 0;\r\n}\r\n");
    	System.out.print(str);
    }
  }
};
```

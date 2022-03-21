# UVA10469：To Carry or not to Carry

## 題目概要

- 將兩個十進位數字轉換為二進位後相加，不管進位的數，將相加後的二進位轉為十進位。

## 解題技巧

- 讀起來很複雜，其實題目的題也解釋了就是個 XOR，所以簡單的做兩數 XOR 就行了。

## 程式碼

我寫完前兩種才想到第三種... 最簡單的作法，差點沒槌死自己。

### 第一種

暴力法，一位數一位數比較，如果一個是 0 一個是 1 就記錄在 Array 中，最後再把 array 中的數字轉換為十進位。

```java
import java.util.*;
import static java.lang.System.*;
public class main {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int x = sc.nextInt();
        int y = sc.nextInt();
        String a = Integer.toBinaryString(x);
        String b = Integer.toBinaryString(y);

        int max = a.length() > b.length() ? a.length() : b.length();
        int num[] = new int[max];

        for(int i = max - 1; i >= 0; i--) {
            if ((a.charAt(i) == '1' && b.charAt(i) == '1') || (a.charAt(i) == '0' && b.charAt(i) == '0')) {
                num[i] = 0;
            } else {
                num[i] = 1;
            }
        }

        int res = 0;
        for(int i = 0; i < num.length; i++) {
             res = res * 10 + num[i];
        }
        String answer = Integer.toString(res);
        System.out.println(Integer.parseInt(answer, 2));
    }
  }
};
```

### 第二種

跟第一種方式差不多，不過是改用次方，用 `Math.pow` 的方式直接轉換為十進位：

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int x = sc.nextInt();
        int y = sc.nextInt();
        String a = Integer.toBinaryString(x);
        String b = Integer.toBinaryString(y);
          int max = a.length() > b.length() ? a.length() : b.length();
          int sum = 0;
          for (int i = 0; i < max; i++) {
              if(a.charAt(i) == '0' && b.charAt(i) == '1') {
                  sum += Math.pow(2, i);
              } else if (a.charAt(i) == '1' && b.charAt(i) == '0') {
                  sum += Math.pow(2, i);
              }
          }
        System.out.println(sum);
    }
  }
};
```

### 第三種

用 JAVA 的位元運算子 XOR 直接做就可以了。

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        int x = sc.nextInt();
        int y = sc.nextInt();

        System.out.println(x ^ y);
    }
  }
};
```

其實位元運算子包括：AND （&）、OR（|）、XOR（^）與補數（~），只不過我們平時比較常使用到 AND 和 OR，所以會忽略 XOR 跟 補數的存在，在關鍵時刻，它們還是很好用的。

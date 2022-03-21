# UVA10473：Simple Base Conversion

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1414)

## 題目概要

- 每行都是一筆測資。

- 將十進位轉為十六進位，將十六進位轉為十進位。

- 如果是負數則結束。

## 解題技巧

- 0x 開頭的字串就從 16 轉 10，否則從 10 轉 16。

- 記熟十六進位轉十進位和十進位轉十六進位的寫法就好了。
  
  - `Integer.decode(x)`：將 x 從**十六進位**轉為**十進位**。
  - `Integer.toHexString`：將**十進位**轉為**十六進位**，但我們接收的值為字串，所以轉換前需要先將字串轉為整數，最後轉換成十六進位後要記得轉大寫，因為輸出結果的英文字要求要大寫。

## 程式碼

```java
public class Uva10473 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    while(sc.hasNext()) {
        String x = sc.next();
        if(x.charAt(0)=='-') break;
        if(x.charAt(0)=='0'){
            System.out.println(Integer.decode(x));
        } else {
            System.out.println("0x" + Integer.toHexString(Integer.parseInt(x)).toUpperCase());
        }
    }
  }
};
```

# UVA10008：What's Cryptanalysis?

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=12&page=show_problem&problem=949)

## 題目概要

- 輸入 N 行字串，計算出所有字母使用的次數，並由大到小輸出。

## 解題技巧

![](https://d1v9pyzt136u2g.cloudfront.net/blog/wp-content/uploads/2021/12/17110601/Ascii_table-1.png)

- 雖然第一行會指定行數，但我們直接用 `sc.hasNext()` 判斷還有沒有字串輸入就好，不然還需要另外去處理，很麻煩。

- 用陣列的方式儲存字母出現的次數，比如 A 的 ASCII code 是 65，就把 **65** 當成 `arr[0]`，那麼 **Z **就是 `arr[25]` 。

- 因為輸出時的英文字母都是大寫，所以紀錄時用**大寫**英文字母的 ASCII Code。

- 字串之間的大於小於比較會以 ASCII code 來比較，所以我們可以藉由 `'A' <= temp.charAt(i) && temp.charAt(i) <= 'Z'` 來得知輸入的字是否為英文字母。

- 字串轉為數字會以 ASCII code 來表現，比如 `(int)A` 就是 65，所以可以藉由 `data[(int)temp.charAt(i) - 65]++` 來記錄英文字母出現的次數。

- 用一個變數 `wordCount` 來記錄輸入的字串總共有多少個字，假設有 20 個字，一個字母最多可能出現的次數就為 20，所以我們可以藉由 `--wordCount > 0` 搭配 for 迴圈遍歷 0 ~ 26 來輸出出現次數最多的字母，當有多個字母出現次數相同時，則按照 A ~ Z 的順序輸出。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class Uva10008 {
  public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int data[] = new int[26];
        int wordCount = 0;

        while(sc.hasNext()) {
            String temp;
            temp = sc.nextLine();
            temp = temp.toUpperCase();
            wordCount += temp.length();
            for(int i = 0; i < temp.length(); i++) {
                if('A' <= temp.charAt(i) && temp.charAt(i) <= 'Z') {
                    data[(int)temp.charAt(i) - 65]++;
                }
            }
        }
        while(--wordCount > 0) {
            for(int i = 0;i < 26; i++) {
                if(data[i] == wordCount) {
                    System.out.println(((char)(i + 65)) + " " + data[i]);
                }
            }
        }
      }
};
```

# UVA10699：Count the factors

[Online Judge](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1640)

## 題目概要

- 每一行皆為一筆測資，最大值為 1,000,000，當輸入 0 時離開。

- 找出一個正整數是有多少個不相同的質因數。

## 解題技巧

- 用遍歷的方式從 2 開始到輸入的數字 X，若 X 能被 i 整除，則將 i 加入 Set 中，最後答案輸出 Set 的長度(`set.size()`)。

## 程式碼

```java
public class Uva10699 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int x;
    while(sc.hasNext() && (x = sc.nextInt()) != 0) {
        Set<Integer> results = new HashSet<Integer>();
        int temp = x; // current number
        int i = 2; // current index (factor)

        while(temp != 1 && i <= temp) { // end if temp equals 1 or i <= temp
            if (temp % i == 0) { // x has the factor i
                results.add(i);
                temp /= i;
            } else {
                i++;
            }
        }
        System.out.println(x + " : " + results.size());
    }
  }
};
```

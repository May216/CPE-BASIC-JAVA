# UVA11917：Do Your Own Homework!

## 題目概要

- Sparrow 給出了她喜歡的科目列表，以及完成每個科目的作業所需的天數。 Soha只有 D 天的時間來完成他的作業。不過還好教授允許可以遲交最多 5 天。 這意味著教授將不接受從現在起 D+5 天之後的任何提交。請求出 Sparrow 能幫 Soha 完成作業嗎？

- 輸入的第一行是代表Case數量。每個Case的第一行為正整數N (1 <= N <= 100)，代表Sparrow可以接受的科目數量。接下來的N行中，每行包含一個科目的名稱，完成該科目的所需天數。  所有科目名稱皆不相同。接下來一行包含一個整數D (1 <= D <= 100)，表示Soha只有D日可以完成他的作業，下面一行包含需要繳交作業的科目名稱。

- 如果Sparrow完成作業所需的時間不超過D天輸出"Yesss"，如果她花了D天以上但不超過D+5天輸出"Late"，如果她花了超過D+5天或者科目她不滿意輸出"Do your own homework!"。

這題 input 有點長，配合範例輸入來看：

```json
3 // case 數量
// 第一筆 case
3 // Sparrow 可接受的科目數
compiler 4 // 科目 完成天數
cplusplus 1
java 8
5 // Soha 有 5 天可以完成作業
compiler // 要繳交的作業科目
// 第二筆 case
2
algorithm 3
math 9
4
math
2
java 8
ai 3
6
calculus
```

## 解題技巧

- 用 Map 存科目和天數。

- 如果不是 Sparrow 願意幫忙做的科目請輸出 `Do your own homework!`

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    for(int i = 1; i <= cases; i++) {
        TreeMap<String, Integer> subjects = new TreeMap<String, Integer>();
        int N = sc.nextInt();

        while(N-- > 0) {
            subjects.put(sc.next(), sc.nextInt()); // Sparrow 願意幫忙做的科目 和 所需花費的時間
        }

        int D = sc.nextInt(); // 限制完成的天數
        String homework = sc.next(); // 作業科目
        System.out.print("Case " + i + ": ");

        if(subjects.get(homework) == null) System.out.println("Do your own homework!"); // 不是 Sparrow 願意幫忙的科目
        else if (D >= subjects.get(homework)) System.out.println("Yesss");
        else if (D + 5 >= subjects.get(homework)) System.out.println("Late");
        else System.out.println("Do your own homework!");
    }
  }
};
```

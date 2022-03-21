# UVA10420：List of Conquests

## 題目概要

- 有 N 筆測資，每筆測資的開頭第一個單詞為國家名稱，後面為人名，我們需要統計所有測資中出現的國家次數，由小到大排序輸出。

## 解題技巧

- 我們可以利用 Map 以 key, value 的形式來存放國家及數量。
  
  - 補充：Java 中的 Map 分為三類 ****Hashtable、HashMap 和 TreeMap***，HashMap & TreeMap 的區別在於，TreeMap 中所有的元素都保持著某種固定的順序，所以當你需要得到一個有序結果時就用 TreeMap (HashMap中元素的排列順序是不固定的)。

- `TreeMap.get()` 方法可以返回指定 key 映射的值；`TreeMap.put()` 方法用於為指定的值與此映射中的指定鍵關聯（若指定鍵原本有值，舊值會被替換）。

- `TreeMap.containsKey()` 方法用於檢查 Map 中是否有包含該鍵值的對映關係。

- `TreeMap.keySet()` 方法用於返回此映射中包含的鍵的 Set，並按照由小到大返回"鍵"。

## 程式碼

一道適合用來練習 TreeMap 的題目。

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt();
    Map<String, Integer> countries = new TreeMap<String, Integer>();

    while(n-- > 0) {
        String country = sc.next();
        if (!countries.containsKey(country)) {
            countries.put(country, 1);
        } else {
            countries.put(country, countries.get(country) + 1);
        }
        sc.nextLine(); // 國家後面的名字用不到
    }

    for(String country: countries.keySet()) {
        System.out.println(country + " " + countries.get(country));
    }
  }
};
```

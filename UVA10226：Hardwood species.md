# UVA10226：Hardwood species

## 題目概要

- 計算出每個物種代表的樹木種群的總比例。

- 第一行會有一個整數 N 代表測資數，後面接著一行空行，每筆測資都包含每棵樹的物種列表，每行代表一個物種。物種名稱不超過 30 個字符，不超過 10,000種物種，不超過 1,000,000 棵樹。

- 按字母順序（ASCII）輸出各物種名稱以及所占百分比，精確到小數點後 4 位。

- 在 2 個連續的測資之間打印一個空行。

## 解題技巧

- 用 treeMap<String, Integer> 來存放物種跟數量。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(sc.hasNextLine()) {
        TreeMap<String, Integer> map = new TreeMap<String, Integer>();
        String species;
        int count = 0; // 物種總數

        while(sc.hasNextLine() && !(species = sc.nextLine()).equals("")) {
            if (map.containsKey(species)) map.put(species, map.get(species) + 1);
            else map.put(species, 1);
            count++;
        }

        for(Object key: map.keySet()) {
            System.out.printf("%s %.4f", key.toString(), map.get(key) * 100.0 / count);
            System.out.println("");
        }
        if(map.size() != 0 && (--cases) > 0) System.out.println("");
    }
  }
};
```

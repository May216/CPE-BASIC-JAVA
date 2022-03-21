# UVA10221：Satellites

## 題目概要

- 地球的半徑為6440公里，若兩顆衛星（在同一軌道上）與地球中心形成一個角度，要求找出兩個衛星之間的距離（弧長和直線距離），請考慮它們是在圓形路徑而不是橢圓路徑上旋轉。
- 每行皆為一筆測資，每筆測資包含兩個整數 s 和 a 以及一個字串 min 或 deg，s 為衛星到地球表面的距離，a 是衛星與地球中心的夾角，以 min 或 deg 為單位。

## 解題技巧

- 用正弦或餘弦可算出兩顆衛星的直線距離，弧長則是用弧長公式計算。
- 當角度超過 180 度時要用 360 去減。
- s 只是衛星到地球的"表面"距離，而我們需要的是衛星到地球"中心"的距離，所以半徑為 r + s。
- 1 min = 60 deg。
- 可使用 `Math.toRadians()` 將角度轉為弧度。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int r = 6440;
    while(sc.hasNext()) {
        double s = sc.nextDouble(), a = sc.nextDouble();
        String type = sc.next();
        if (type.equals("deg")) Math.min(360 - a, a);
        else a /= 60;

        double R = s + r; // radius
        a = Math.toRadians(a); // convert degrees to radians

        double arc = R * a;
        double chrod = Math.sqrt(2 * Math.pow(R, 2) * (1 - Math.cos(a)));
        System.out.printf("%.6f %.6f\r\n", arc, chrod);
    }
  }
};
```

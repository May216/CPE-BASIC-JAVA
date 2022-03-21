# UVA11342：Three-Square

## 題目概要

- 給定一個正整數 K ( <= 50000 )，求出 $K = a^2 + b^2 + c^2$ 的 a,b,c 為多少，如果無法算出則輸出 -1

## 解題技巧

- 無

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt();
    while(cases-- > 0) {
        double k = sc.nextDouble();
        Vector<Integer> vector = new Vector<Integer>();
        boolean flag = false;
        int powM = (int)Math.sqrt(k); //找出k的整數根號。

        //找出a^2+b^2+c^2=k。
        for(int j = 0; j <= powM; j++){
            double tempK = k - (j*j); //b^2+c^2=k-a^2。
            for(int z = 0; z <= powM; z++){
                double tempK2 = tempK - (z*z); //c^2=k-b^2。
                int temp = (int)Math.sqrt(tempK2);
                //當c可以開成整數根號時，代表符合題意。
                if((temp*temp)==(int)tempK2){
                    vector.add(j);
                    vector.add(z);
                    vector.add(temp);
                    flag = true;
                    break;
                }
            }
            if(flag) break;
        }

        //Output
        if(vector.size() == 3) System.out.println(vector.get(0)+" "+vector.get(1)+" "+vector.get(2));
        else System.out.println("-1");
    }
  }
};
```

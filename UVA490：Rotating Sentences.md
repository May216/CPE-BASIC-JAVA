# UVA490：Rotating Sentences

## 題目概要

- 如題目所說，將字串轉 90 度後輸出。

- 最多 100 個句子，每句不超過 100 個字符，所以可以建一個 101 * 101 的二維陣列。

## 解題技巧

- 用二維陣列儲存。

## 程式碼

```java
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
  	Scanner sc = new Scanner(System.in);
	char[][] str = new char[101][101];
	int[] length = new int[101];
	int lines = 0, maxlen = 0;
	while(sc.hasNextLine()) {
		String s = sc.nextLine();
		str[lines] = s.toCharArray();
		length[lines] = s.length(); // 紀錄每行字數
		if(length[lines] > maxlen) // 紀錄所有行的最大字數
			maxlen = length[lines];
		lines ++;
	}
	int count = 0; // 用於判斷需要補幾個 0
	for(int i = 0; i < maxlen; i++) {
		count = 0;
		for(int j = lines - 1; j >= 0; j--){ // 轉 90 度, 即從最後一行最左邊, 往上一行輸出, 由下至上, 由左至
			if(!(i >= length[j])) { // 當某行字串結束時，不再印出字
				while(count > 0) {
					System.out.print(" ");
					count--;
				}
				System.out.print(str[j][i]);
				count = 0;
			} else count++;
		}
		System.out.println();
	}
  }
};
```

# UVA10258：Contest Scoreboard

## 題目概要

- 根據 input 計算出最後排名順序。

- 第一行代表有 N 筆測資，測資後跟一行空白。

- 接下來的每行皆有三格空格空開資料，分別為：隊伍編號、提交題號、所花時間、結果。

- 結果分為：C、I、R、U、E，只有結果等於 C 時才能計算時間，否則將記錄錯誤次數 (I) 直到答對為止，時間計算方式為：錯誤次數 * 20 + 答對所花時間。R、U、E 不做任何事。

- 若已經答對的題目不再做計算，排名方式依據答對總題數最多→耗時最少→隊伍編號(大到小) 輸出。

- 題數不超過 100 題。

## 解題技巧

- 需要用到物件封裝的概念，建立一個物件 Data，用於記錄錯誤題數、計算花費時間、獲取隊伍號碼、獲取答對題數、獲取當前花費時間、獲取當前錯誤題數...等。

- 用 Vector 存放結果，Vector 是一個可放入任何型態的動態陣列(等同於 ArrayList)，所以我們可以將自定義的 Data 放入 Vector 中，方便後續的計算。

## 程式碼

```java
import java.util.*;
import static java.lang.System.*;
public class main{
  public static void main(String[] args) {
      Scanner sc = new Scanner(System.in);
    int cases = sc.nextInt() - 1; //總共多少Case
    String empty = sc.nextLine(); //先讀取第一行空白
    while(sc.hasNextLine()){
        String st;
        Vector<Data> vector = new Vector<Data>();
        while(sc.hasNextLine() && !(st = sc.nextLine()).equals("")){
            String temp[] = st.split("\\s+"); //把隊伍編號、所答的題目編號、時間、結果分開
            boolean flag = false; //判斷隊伍資料是否已經建立
            for(int i = 0; i < vector.size(); i++){
                if(vector.get(i).getTeamNo() == Integer.parseInt(temp[0])){
                    if(temp[3].equals("C")) vector.get(i).countTime(Integer.parseInt(temp[1]), Integer.parseInt(temp[2])); //當結果為 C 時計算時間
                    else if(temp[3].equals("I")) vector.get(i).setError(Integer.parseInt(temp[1])); //當結果為 I 時紀錄錯誤次數
                    flag = true;
                    break;
                }
            }
            if(vector.isEmpty() || !flag){
                Data data = new Data(Integer.parseInt(temp[0]));
                if(temp[3].equals("C")) data.countTime(Integer.parseInt(temp[1]), Integer.parseInt(temp[2])); //當結果為 C 時計算時間
                else if(temp[3].equals("I")) data.setError(Integer.parseInt(temp[1])); //當結果為 I 時紀錄錯誤次數
                vector.add(data); 
            }
        }

        while(!vector.isEmpty()){
            int index = 0;
            Data data = vector.firstElement();
            //名次表較依(答對)總題數最多→時間最少→隊伍編號
            for(int i = 0; i < vector.size(); i++){
                if(data.getC() < vector.get(i).getC()){ // c = correct number
                    data = vector.get(i);
                    index = i;
                }else if(data.getC() == vector.get(i).getC()){
                    if(data.getTime() > vector.get(i).getTime()){
                        data = vector.get(i);
                        index = i;
                    }else if(data.getTime() == vector.get(i).getTime()){
                        if(data.getTeamNo() > vector.get(i).getTeamNo()){
                            data = vector.get(i);
                            index = i;
                        }
                    }
                }
            }
            //Output
            System.out.println(vector.get(index).getTeamNo() + " " + vector.get(index).getC() + " " + vector.get(index).getTime());
            vector.remove(index); //印出資料後就刪除
            if(vector.size() == 0 && (cases--) > 0) System.out.println("");
        }

    }
  }
};

class Data {
    private int teamNo; //隊伍編號
    private int time; //目前隊伍所花的時間
    private int c; //答對題數
    private boolean problem[] = new boolean[100]; //題目是否已經答對
    private int error[] = new int[100]; //題目錯誤次數
    Data(){ // init
        teamNo = 0;
        time = 0;
        c = 0;
        Arrays.fill(problem, false); // 每題預設為未答對
        Arrays.fill(error, 0); // 每題預設答錯 0 次
    }
    Data(int teamNo){
        this.teamNo = teamNo;
    }
    public void setError(int No){
        error[No - 1]++;
    }
    public void countTime(int problemNo, int time){
        if(!problem[problemNo - 1]){
            c++;
            this.time += (time + error[problemNo - 1] * 20);
            problem[problemNo - 1] = true;
        }
    }
    public int getTeamNo(){
        return teamNo;
    }
    public int getC(){
        return c;
    }
    public int getTime(){
        return time;
    }
    public void errorNum(){
        for(int i = 0; i < 100; i++){
            System.out.println(error[i]);
        }
    }
}
```

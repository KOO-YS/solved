# [BaekJoon#1074] Z



> ### Problem
>
> https://www.acmicpc.net/problem/1074



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = (int)Math.pow(2, Integer.parseInt(tokenizer.nextToken()));

        int r = Integer.parseInt(tokenizer.nextToken())+1;
        int c = Integer.parseInt(tokenizer.nextToken())+1;

        int count = findVisitOrder(r, c, 0, 0, N) - 1;

        System.out.println(count);

    }

    public static int findVisitOrder(int r, int c, int startX, int startY, int term){
        int half = term/2;
        int halfX = startX + half;
        int halfY = startY + half;

        Division division;

        if(r > halfX){
            if(c > halfY){
                division = Division.FOUR;
            }else {
                division = Division.THREE;
            }
        } else {
            if(c > halfY){
                division = Division.TWO;
            }else {
                division = Division.ONE;
            }
        }

        if(term == 2){
            return division.getNum();
        } else{
            return division.getBefore()*(int)Math.pow(half, 2)
                    + findVisitOrder(r, c, division.setStartX(startX, term), division.setStartY(startY, term), term/2);
        }
    }
}

/**
 * 배열을 4등분 했을 때 방문하는 순서
 */
enum Division{
    ONE(1), TWO(2), THREE(3), FOUR(4);

    int num;

    Division(int num) {
        this.num = num;
    }

    public int getBefore(){
        return this.num - 1;
    }

    public int getNum(){
        return this.num;
    }

    public int setStartX(int startX, int term){
        if(this == ONE || this == TWO){
            return startX;
        } else return startX + term/2;
    }

    public int setStartY(int startY, int term){
        if(this == ONE || this == THREE){
            return startY;
        } else return startY + term/2;
    }
}
```

# [BaekJoon#2488] 별 찍기 11



> ### Problem
>
> https://www.acmicpc.net/problem/2488



> ### Solution

```java
import java.io.*;
import java.util.Arrays;

class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        System.out.print(printStars(N));
    }
    public static String printStars(int N){
        StringBuilder line = new StringBuilder();

        // setting
        star = new char[N][2*N-1];
        for(char[] s : star){
            Arrays.fill(s, ' ');
        }
        
        // when
        triangle(N, 0, 0);

        // then
        for(char[] l : star){
            for(char ch : l){
                line.append(ch);
            }
            line.append('\n');
        }

        return line.toString();
    }
    public static char[][] basic = {
            {' ', ' ', '*', ' ', ' '},
            {' ', '*', ' ', '*', ' '},
            {'*', '*', '*', '*', '*'}
    };
    public static char[][] star;

    public static void triangle(int line, int x, int y){
        if(line == 3){
            for(int i=0; i<3; i++){
                for(int j=0; j<5; j++){
                    star[x+i][y+j] = basic[i][j];
                }
            }
            return;
        }
        int half = line/2;

        triangle(half, x, y + half);

        for(int i=0; i<3; i++){
            if(i == 1) continue;
            triangle(half, x+half, y+i*half);
        }
    }
}
```

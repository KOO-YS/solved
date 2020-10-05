# [BaekJoon#1937] 욕심쟁이 판다



> ### Problem
>
> https://www.acmicpc.net/problem/1937



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static int[] dx = {0, -1, 0, 1};
    public static int[] dy = {-1, 0, 1, 0};
    public static int[][] forest;
    public static int[][] days;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());

        StringTokenizer token;
        forest = new int[n][n];
        days = new int[n][n];

        for(int i=0; i<n; i++){
            token = new StringTokenizer(br.readLine(), " ");
            for(int j=0; j<n; j++){
                forest[i][j] = Integer.parseInt(token.nextToken());
                days[i][j] = -1;
            }
        }
        int max = 0;
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                dfs(i, j);
                if(days[i][j]>max) max = days[i][j];
            }
        }
        System.out.println(max);
    }
    public static int dfs(int i, int j){
        int day = 1;
        int bamboo = forest[i][j];
        if(days[i][j] != -1) return days[i][j];
        for(int d=0; d<4; d++){
            int x = i + dx[d];
            int y = j + dy[d];
            if(isValid(x,y) && forest[x][y] > bamboo) {
                day = Math.max(day, dfs(x, y) + 1);
            }
        }
        return days[i][j] = day;
    }
    public static boolean isValid(int i, int j){
        if(i<0 || j<0 || i>= forest.length || j>= forest[i].length) return false;
        return true;
    }
}
```
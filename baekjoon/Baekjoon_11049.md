# [BaekJoon#11049] 최소 행렬 곱셈



> ### Problem
>
> https://www.acmicpc.net/problem/11049



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static int[][] matrix;
    public static int[][] dp;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;
        int N = Integer.parseInt(br.readLine());

        matrix = new int[N][2];
        dp = new int[N][N];

        for(int i=0; i<N; i++){
            token = new StringTokenizer(br.readLine(), " ");
            matrix[i][0] = Integer.parseInt(token.nextToken());
            matrix[i][1] = Integer.parseInt(token.nextToken());
        }

        multipleMin(0, N-1);
        System.out.println(dp[0][N-1]);

    }
    public static int multipleMin(int start, int end){
        int min = Integer.MAX_VALUE;
        if(start == end) return 0;

        if(dp[start][end] != 0) return dp[start][end];

        for(int i=start; i<end; i++){
            min = Math.min(min, multipleMin(start, i)+multipleMin(i+1, end)+matrix[start][0]*matrix[i][1]*matrix[end][1]);
            dp[start][end] = min;
        }
        return min;
    }
}
```

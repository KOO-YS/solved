# [BaekJoon#7579] 앱



> ### Problem
>
> https://www.acmicpc.net/problem/7579

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static int MAX = 10001;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token = new StringTokenizer(br.readLine());

        // 활성화 되어있는 N개의 앱
        int N = Integer.parseInt(token.nextToken());
        // 추가적으로 필요한 M 메모리
        int M = Integer.parseInt(token.nextToken());

        int[] memory = new int[N];
        int[] cost = new int[N];
        int[][] dp = new int[N][MAX];

        int answer = 10001;

        StringTokenizer memoryToken = new StringTokenizer(br.readLine(), " ");
        StringTokenizer costToken = new StringTokenizer(br.readLine(), " ");

        for(int i=0; i<N; i++){
            memory[i] = Integer.parseInt(memoryToken.nextToken());
            cost[i] = Integer.parseInt(costToken.nextToken());
        }
        for(int i=0; i<N; i++){
            int c = cost[i];
            int m = memory[i];

            for(int j=0; j<MAX; j++){
                if(i == 0){
                    if(j >= c) dp[i][j] = m;
                } else {
                    if(j >= c){
                        dp[i][j] = Math.max(dp[i-1][j-c]+m, dp[i-1][j]);
                    } else dp[i][j] = dp[i-1][j];
                }

                if(dp[i][j] >= M) answer = Math.min(answer, j);
            }
        }

        System.out.println(answer);
    }

}
```

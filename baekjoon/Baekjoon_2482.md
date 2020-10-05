# [BaekJoon#2482] 색상환



> ### Problem
>
> https://www.acmicpc.net/problem/2482



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static int MAX = 10001;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());
        int K = Integer.parseInt(br.readLine());
        /*
        * CASE 1.
        * i개에서 마지막 j번째 칸을 선택할 경우
        * -> i-2 개의 칸에서 j-1개를 추가로 골라야 한다
        *
        * CASE 2.
        * i개에서 마지막 j번째를 선택하지 않았을 경우
        * -> i-1 개의 칸에서 j개를 골라야 한다
        *
        * dp[i][j] = dp[i-2][j-1] + dp[i-1][j]
        */
        int[][] dp = new int[1001][1001];
        for(int i=1; i<=N; i++){
            dp[i][1] = i;       // i개에서 1개를 고르는 경우의 수는 i 
            dp[i][0] = 1;       // 아무것도 고르지 않는 경우는 1로 초기화
        }
        for(int i=2; i<=N; i++ ){
            for(int j=2; j<=K; j++){
                dp[i][j] = dp[i][j] = (dp[i-2][j-1] + dp[i-1][j]) % 1000000003;
            }
        }
        
        /*
        * N개 중 K개를 선택해야한다면?
        * N번째를 선택한 경우 -> 1번째, N번째, N-1번째를 뺸 N-3개에서 K-1개를 선택 해야함
        * N번째를 선택하지 않은 경우 -> N-1개에서 K개를 선택 해야함
        */
        int answer = ( dp[N-3][K-1] + dp[N-1][K] ) % 1000000003;
        System.out.println(answer);
    }

}
```



> ##### 참고
>
> https://akim9905.tistory.com/71
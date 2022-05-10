# [BaekJoon#1932] 정수 삼각형



> ### Problem
>
> https://www.acmicpc.net/problem/1932



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;

        int n = Integer.parseInt(br.readLine());
        int[][] triangle = new int[n][n];

        for(int row=0; row<n; row++) {
            tokenizer = new StringTokenizer(br.readLine(), " ");
            for(int i=0; i<=row; i++) {
                triangle[row][i] = Integer.parseInt(tokenizer.nextToken());
            }
        }

        for(int row=n-1; row>0; row--) {
            for(int i=0; i<row; i++) {
                triangle[row-1][i] += Math.max(triangle[row][i], triangle[row][i+1]);
            }
        }

        System.out.println(triangle[0][0]);
    }
}
```

# [BaekJoon#14502] 연구소



> ### Problem
>
> https://www.acmicpc.net/problem/14502


> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

//https://www.acmicpc.net/problem/14502
class Main {

    public static int N;
    public static int M;
    public static int[][] map;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        N = Integer.parseInt(tokenizer.nextToken());
        M = Integer.parseInt(tokenizer.nextToken());

        map = new int[N][M];

        for (int i=0; i<N; i++) {
            tokenizer = new StringTokenizer(br.readLine());
            for (int j=0; j<M; j++) {
                map[i][j] = Integer.parseInt(tokenizer.nextToken());
            }
        }
    }
}
```
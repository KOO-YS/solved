# [BaekJoon#1149] RGB 거리



> ### Problem
>
> https://www.acmicpc.net/problem/1149



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {
    public static int RED = 0;
    public static int GREEN = 1;
    public static int BLUE = 2;

    public static int[][] minCost;
    public static int[][] houses;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;

        int N = Integer.parseInt(br.readLine());

        houses = new int[N][3];

        for(int i=0; i<N; i++){
            tokenizer = new StringTokenizer(br.readLine());

            houses[i][RED] = Integer.parseInt(tokenizer.nextToken());
            houses[i][GREEN] = Integer.parseInt(tokenizer.nextToken());
            houses[i][BLUE] = Integer.parseInt(tokenizer.nextToken());
        }

        minCost = new int[N][3];

        minCost[0][RED] = houses[0][RED];
        minCost[0][GREEN] = houses[0][GREEN];
        minCost[0][BLUE] = houses[0][BLUE];

        for(int i=1; i<N; i++){
            // 이번 차례에서 RED 색을 칠할 경우 -> 이전에 GREEN, BLUE를 칠했어야 한다
            minCost[i][RED] = Math.min(minCost[i-1][GREEN], minCost[i-1][BLUE]) + houses[i][RED];
            minCost[i][GREEN] = Math.min(minCost[i-1][RED], minCost[i-1][BLUE]) + houses[i][GREEN];
            minCost[i][BLUE] = Math.min(minCost[i-1][RED], minCost[i-1][GREEN]) + houses[i][BLUE];
        }

        int min = Math.min(minCost[N-1][RED], minCost[N-1][GREEN]);
        min = Math.min(min, minCost[N-1][BLUE]);

        System.out.print(min);
    }
}
```

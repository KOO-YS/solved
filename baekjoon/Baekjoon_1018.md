# [BaekJoon#1018] 체스판 다시 칠하기



> ### Problem
>
> https://www.acmicpc.net/problem/1018



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static int MIN;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(tokenizer.nextToken());
        int M = Integer.parseInt(tokenizer.nextToken());

        MIN = Integer.MAX_VALUE;
        // 0, 0 이 black or white
        char[][] chess = new char[N][M];
        for (int i=0; i<N; i++) {
            char[] line = br.readLine().toCharArray();
            System.arraycopy(line, 0, chess[i], 0, N);
        }

        for (int i=0; i<N-8; i++) {
            for (int j=0; j<M-8; j++) {
                MIN = Math.min(MIN, make8square(i, j, chess[i][j]));
            }
        }
        System.out.println(MIN);
    }

    public static int make8square(int startH, int startW, char startChar) {
        int count = 0;

        for (int i=startH; i<startH+8; i++) {
            for (int j=startW; j<startW+8; j++) {



            }
        }
        return count;
    }


}

```

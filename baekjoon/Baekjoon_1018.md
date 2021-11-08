# [BaekJoon#1018] 체스판 다시 칠하기



> ### Problem
>
> https://www.acmicpc.net/problem/1018



> ### Solution WRONG
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static char[][] chess;
    public static int MIN;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(tokenizer.nextToken());
        int M = Integer.parseInt(tokenizer.nextToken());

        MIN = Integer.MAX_VALUE;
        // 0, 0 이 black or white
        chess = new char[N][M];
        for (int i=0; i<N; i++) {
            char[] line = br.readLine().toCharArray();
            System.arraycopy(line, 0, chess[i], 0, N);
        }

        for (int i=0; i<N-7; i++) {
            for (int j=0; j<M-7; j++) {
                MIN = Math.min(MIN, make8square(i, j, chess[i][j], 'B'));
                MIN = Math.min(MIN, make8square(i, j, chess[i][j], 'W'));
            }
        }
        System.out.println(MIN);
    }

    public static int make8square(int startH, int startW, char startChar, char standard) {
        if(startW==14 && startH==1) System.out.println("TOUCH");
        int count = 0;
        boolean sameWithStart = (startChar == standard);
        for (int i=startH; i<startH+8; i++) {
            if(i == startH+7) System.out.println("t");
            for (int j=startW; j<startW+8; j++) {
                if (sameWithStart != (chess[i][j] == standard))
                    count++;
                sameWithStart = !sameWithStart;
            }
            sameWithStart = !sameWithStart;
        }
        return count;
    }
}
```

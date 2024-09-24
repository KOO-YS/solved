# [BaekJoon#10709] 기상캐스터



> ### Problem
>
> https://www.acmicpc.net/problem/10709



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int H = Integer.parseInt(tokenizer.nextToken());
        int W = Integer.parseInt(tokenizer.nextToken());

        int[][] sky = new int[H][W];
        for (int i=0; i<H; i++) {
            Arrays.fill(sky[i], -1);

            char[] clouds = br.readLine().toCharArray();
            int index = -1;
            for (int j=0; j<W; j++) {
                if (clouds[j] == 'c') {
                    index = 0;
                    sky[i][j] = index;
                    index ++;
                } else if (index > 0) {
                    sky[i][j] = index;
                    index ++;
                }
            }
        }

        for (int i=0; i<H; i++) {
            for (int j=0; j<W; j++)
                System.out.print(sky[i][j] + " ");
            System.out.println();
        }
    }
}
```


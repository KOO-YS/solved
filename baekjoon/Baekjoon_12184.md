# [BaekJoon#12184] GBus count (Small)



> ### Problem
>
> https://www.acmicpc.net/problem/12184



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    // https://www.acmicpc.net/problem/12184
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine()); // the number of Test case

        for (int t=1; t <= T; t++) {
            result.append("Case #"+t+": ");
            int N = Integer.parseInt(br.readLine()); // the number of GBuses

            int [][] ranges = new int[N][2];
            tokenizer = new StringTokenizer(br.readLine(), " ");
            for (int i=0; i<N; i++) {
                ranges[i][0] = Integer.parseInt(tokenizer.nextToken());
                ranges[i][1] = Integer.parseInt(tokenizer.nextToken());
            }

            int P = Integer.parseInt(br.readLine());

            for (int i=0; i<P; i++) {
                // 해당 씨디에 대한 계산 값
                int buses = 0;
                result.append(buses + " ");
            }
            br.readLine();
            result.append('\n');
        }
        System.out.println(result);
    }
}

```

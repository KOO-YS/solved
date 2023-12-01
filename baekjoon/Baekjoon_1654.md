# [BaekJoon#1654] 랜선 자르기



> ### Problem
>
> https://www.acmicpc.net/problem/1654



> ### Solution
>
 ```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(tokenizer.nextToken());
        int K = Integer.parseInt(tokenizer.nextToken());


        int[] lines = new int[N];
        int max = 0;
        for (int i=0; i<N; i++) {
            lines[i] = Integer.parseInt(br.readLine());
            max = Math.max(max, lines[i]);
        }

        int start = 0;
        int end = max + 1;
        int count;
        while (start < end) {
            int mid = (start + end)/2;
            count = 0;
            for (int i=0; i<N; i++) {
                count += (lines[i]/mid);
            }
            if (count < K) {
                end = mid;
            } else
                start = mid + 1;
        }

        System.out.println(start-1);

    }
    
}
```


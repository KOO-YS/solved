# [BaekJoon#10816] 숫자 카드 2



> ### Problem
>
> https://www.acmicpc.net/problem/10816



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;
        StringBuilder result = new StringBuilder();

        int[] plus = new int[10000001];
        int[] minus = new int[10000001];

        int N = Integer.parseInt(br.readLine());

        tokenizer = new StringTokenizer(br.readLine());
        for (int i=0; i<N; i++) {
            int num = Integer.parseInt(tokenizer.nextToken());
            if (num >= 0) {
                plus[num]++;
            } else minus[Math.abs(num)]++;
        }

        int M = Integer.parseInt(br.readLine());
        tokenizer = new StringTokenizer(br.readLine());
        for (int i=0; i<M; i++) {
            int num = Integer.parseInt(tokenizer.nextToken());
            if (num >= 0) {
                result.append(plus[num]);
            } else result.append(minus[Math.abs(num)]);
            result.append(' ');
        }
        System.out.println(result.toString());
    }
}
```

<br>



#### 이항 계수 뜻 

-> 조합 (N개 중에서 M개를 뽑는 경우의 수)

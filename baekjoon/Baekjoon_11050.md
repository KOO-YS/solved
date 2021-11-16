# [BaekJoon#11050] 이항 계수 1



> ### Problem
>
> https://www.acmicpc.net/problem/11050



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(tokenizer.nextToken());
        int M = Integer.parseInt(tokenizer.nextToken());

        /*- operation :  n! / (m! * (n-m)!) -*/
        int result = factorial(N)/(factorial(M) * factorial(N-M));
        System.out.println(result);

    }
    public static int factorial(int n) {
        if (n == 1 || n == 0) return 1;
        return factorial(n-1) * n;
    }
}
```

<br>



#### 이항 계수 뜻 

-> 조합 (N개 중에서 M개를 뽑는 경우의 수)

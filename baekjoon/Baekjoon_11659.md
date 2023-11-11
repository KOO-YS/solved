# [BaekJoon#11659] 구간 합 구하기 4



> ### Problem
>
> https://www.acmicpc.net/problem/11659



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());

        int[] arr = new int[N];
        int[] sum = new int[M];

        token = new StringTokenizer(br.readLine());
        for (int i=0; i<N; i++) {
            arr[i] = Integer.parseInt(token.nextToken());
            if (i > 0)
                arr[i] += arr[i-1];
        }

        for (int i=0; i<M; i++) {
            token = new StringTokenizer(br.readLine());
            sum[i] = prefixSum(arr, Integer.parseInt(token.nextToken()), Integer.parseInt(token.nextToken()));
        }

        Arrays.stream(sum).forEach(System.out::println);

    }

    public static int prefixSum(int[] arr, int start, int end) {
        int result = arr[end-1];

        if (start != 1)
            result -= arr[start-2];

        return result;
    }
}
```

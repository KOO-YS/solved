# [BaekJoon#15655] N과 M (6)



> ### Problem
>
> https://www.acmicpc.net/problem/15655



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static int N;
    public static int M;
    public static boolean[] visited;

    public static int[] numbers;
    public static int[] sequence;

    public static StringBuilder result;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());
        result = new StringBuilder();

        N = Integer.parseInt(tokenizer.nextToken());
        M = Integer.parseInt(tokenizer.nextToken());

        visited = new boolean[N];
        numbers = new int[N];
        sequence = new int[M];

        tokenizer = new StringTokenizer(br.readLine());
        for (int i=0; i<N; i++) {
            numbers[i] = Integer.parseInt(tokenizer.nextToken());
        }
        Arrays.sort(numbers);

        getSequence(0, 0);

        System.out.println(result);
    }

    public static void getSequence(int index, int m) {
        if (m == M) {
            Arrays.stream(sequence).forEach(i -> result.append(i).append(' '));
            result.append('\n');
            return;
        }
        for (int i=index; i<N; i++) {
            if (!visited[i]) {
                visited[i] = true;
                sequence[m] = numbers[i];
                getSequence(i, m + 1);
                visited[i] = false;
            }
        }
    }
}
```


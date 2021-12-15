# [BaekJoon#10989] 수 정렬하기 3



> ### Problem
>
> https://www.acmicpc.net/problem/10989



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        int[] num = new int[N];

        for (int i=0; i<N; i++) {
            num[i] = Integer.parseInt(br.readLine());
        }
        Arrays.sort(num);

        for (int i : num) {
            result.append(i).append('\n');
        }
        System.out.print(result.toString());
    }
}
```

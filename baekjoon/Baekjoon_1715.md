# [BaekJoon#1715] 카드 정렬하기



> ### Problem
>
> https://www.acmicpc.net/problem/1715



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.PriorityQueue;
import java.util.Queue;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        Queue<Integer> queue = new PriorityQueue<>();

        for (int i=0; i<N; i++) {
            queue.add(Integer.parseInt(br.readLine()));
        }
        int answer = 0;
        int A, B;
        while (queue.size() != 1) {
            A = queue.remove();
            B = queue.remove();

            answer += A + B;
            queue.add(A + B);
        }
        System.out.println(answer);
    }
}
```


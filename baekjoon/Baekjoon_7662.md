# [BaekJoon#7662] 이중 우선순위 큐



> ### Problem
>
> https://www.acmicpc.net/problem/7662



> ### Solution

```java

```

<br>



> ### 오답 -> 시간초과

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    public static StringTokenizer tokenizer;
    public static void main(String[] args) throws Exception {
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());
        int k;
        int[] arr;
        while (T-- > 0) {
            k = Integer.parseInt(br.readLine());
            if((arr = operate(k)) == null) {
                result.append("EMPTY");
            } else result.append(arr[0]).append(' ').append(arr[1]);
            result.append('\n');
        }
        System.out.print(result.toString());
    }

    public static int[] operate(int k) throws IOException {
        Queue<Integer> p = new PriorityQueue<>();
        Deque<Integer> queue = new ArrayDeque<>();

        char cmd;
        int num;
        while (k-- >0) {
            tokenizer = new StringTokenizer(br.readLine());
            cmd = tokenizer.nextToken().charAt(0);
            num = Integer.parseInt(tokenizer.nextToken());

            if (cmd == 'D') {
                if(num > 0)
                    queue.pollLast();
                else
                    queue.pollFirst();
            } else {
                queue.add(num);

                p.clear();
                p.addAll(queue);

                queue.clear();
                queue.addAll(p);
            }
        }

        return queue.isEmpty()? null : new int[]{queue.peekFirst(), queue.peekLast()};
    }
}
```

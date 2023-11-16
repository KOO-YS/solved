# [BaekJoon#11286] 절댓값 힙



> ### Problem
>
> https://www.acmicpc.net/problem/11286



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.PriorityQueue;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());

        PriorityQueue<Integer> queue = new PriorityQueue<Integer>((o1, o2) -> {
            if (Math.abs(o1) < Math.abs(o2))
                return -1;
            else if (Math.abs(o1) > Math.abs(o2))
                return 1;
            else {
                return (o1 < o2)? -1 : 1;
            }
        });

        StringBuilder result = new StringBuilder();
        int input;
        while (N-- > 0) {
            input = Integer.parseInt(br.readLine());

            if (input == 0) {
                if (queue.isEmpty())
                    result.append("0\n");
                else
                    result.append(queue.poll()).append('\n');
            } else
                queue.add(input);
        }

        System.out.println(result);

    }
}
```

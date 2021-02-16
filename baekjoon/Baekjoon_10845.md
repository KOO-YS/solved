# [BaekJoon#10845] 큐

> ### Problem
>
> https://www.acmicpc.net/problem/10845



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Deque;
import java.util.LinkedList;
import java.util.NoSuchElementException;
import java.util.StringTokenizer;

public class Main {
    public static StringBuilder result = new StringBuilder();
    public static Deque<Integer> queue = new LinkedList<>();

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        for(int i=0; i<N; i++){
            command(br.readLine());
        }

        System.out.print(result.toString());

    }

    public static void command(String str){
        StringTokenizer tokenizer = new StringTokenizer(str, " ");

        String cmd = tokenizer.nextToken();

        try {
            switch (cmd) {
                case "push":
                    queue.add(Integer.parseInt(tokenizer.nextToken()));
                    break;
                case "pop":
                    result.append(queue.remove()).append("\n");
                    break;
                case "size":
                    result.append(queue.size()).append("\n");
                    break;
                case "empty":
                    result.append(queue.isEmpty() ? 1 : 0).append("\n");
                    break;
                case "front":
                    result.append(queue.getFirst()).append("\n");
                    break;
                case "back":
                    result.append(queue.getLast()).append("\n");
                    break;
            }
        } catch (NoSuchElementException e){
            result.append("-1").append("\n");
        }
    }
}
```

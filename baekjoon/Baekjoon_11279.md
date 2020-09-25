# [BaekJoon#11279] 최대 힙



> ### Problem
>
> https://www.acmicpc.net/problem/11279

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Comparator;
import java.util.PriorityQueue;
import java.util.Queue;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuffer result = new StringBuffer();
        int N = Integer.parseInt(br.readLine());

        Queue<Integer> queue = new PriorityQueue<>(Comparator.reverseOrder());

        String input;
        while(N-->0){
            input = br.readLine();
            if(input.equals("0")){
                if(queue.isEmpty()){
                    result.append(0);
                } else {
                    result.append(queue.poll());
                }
                result.append("\n");
            } else {
                queue.add(Integer.parseInt(input));
            }
        }
        System.out.println(result.toString());
    }
}
```

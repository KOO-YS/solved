# [BaekJoon#1927] 최소 힙



> ### Problem
>
> https://www.acmicpc.net/problem/1927



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.PriorityQueue;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());
        PriorityQueue<Integer> queue = new PriorityQueue<>();

        for(int i=0; i<N; i++){
            int num = Integer.parseInt(br.readLine());

            if(num == 0){
                if(queue.isEmpty()){
                    result.append("0\n");
                } else {
                    result.append(queue.poll()).append("\n");
                }
            } else {
                queue.add(num);
            }
        }

        System.out.print(result.toString());
    }
}
```

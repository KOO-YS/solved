# [BaekJoon#11866] 요세푸스 문제 0



> ### Problem
>
> https://www.acmicpc.net/problem/11866



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        StringTokenizer tokenizer = new StringTokenizer(br.readLine(), " ");

        int N = Integer.parseInt(tokenizer.nextToken());
        int K = Integer.parseInt(tokenizer.nextToken());

        Queue<Integer> josephus = new LinkedList<>();
        // init
        for(int i=1; i<=N; i++){
            josephus.add(i);
        }

        result.append("<");

        int turn = 0;
        while(!josephus.isEmpty()){
            turn++;
            if(turn == K){
                result.append(josephus.poll()).append(", ");
                turn = 0;
            } else {
                josephus.add(josephus.poll());
            }
        }
        result.delete(result.length()-2, result.length());      // 마지막 쉼표+공백 제거
        result.append(">");
        System.out.println(result.toString());
    }
}
```

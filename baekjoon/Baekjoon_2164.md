# [BaekJoon#2164] 카드 2



> ### Problem
>
> https://www.acmicpc.net/problem/2164

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        if(N == 1) {
            System.out.println(1);
            return;
        }
        Queue<Integer> cards = new LinkedList<>();

        // 첫번째는 삭제되고 두번째는 뒤로 넘긴다 -> 곧 짝수만 남는다(초기 세팅)
        for(int i=2; i<=N; i+=2) {
            cards.add(i);
        }
        // 만약 N이 홀수라면 N이 삭제되고 가장 앞에 있는 짝수가 끝으로 간다
        if(N%2 == 1) {
            cards.add(cards.poll());
        }

        while(cards.size()>1){
            cards.poll();
            cards.add(cards.poll());
        }
        System.out.println(cards.poll());

    }
}
```

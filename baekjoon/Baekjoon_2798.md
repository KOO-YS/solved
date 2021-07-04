# [BaekJoon#2798] 블랙잭



> ### Problem
>
> https://www.acmicpc.net/problem/2798



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine(), " ");

        int N = Integer.parseInt(tokenizer.nextToken());
        int M = Integer.parseInt(tokenizer.nextToken());

        int[] cards = new int[N];

        tokenizer = new StringTokenizer(br.readLine(), " ");

        int over = 0;   // 이미 M을 넘어 합을 만들 수 없는 수 개수
        for(int i=0; i<N; i++) {
            cards[i] = Integer.parseInt(tokenizer.nextToken());
            if(cards[i] >= M) over++;
        }

        Arrays.sort(cards);

        int max = 0;

        int index = N-over-1;
        int sum;
        for(int i=index; i>=2; i--) {
            for(int j=i-1; j>=1; j--) {
                for(int k=j-1; k>=0; k--) {
                    sum = cards[i] + cards[j] + cards[k];
                    if(sum == M) {
                        System.out.println(M);
                        return;
                    }
                    else if(sum < M) max = Math.max(sum, max);
                }
            }
        }
        System.out.println(max);
    }
}
```


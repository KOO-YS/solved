# [BaekJoon#10815] 숫자 카드



> ### Problem
>
> https://www.acmicpc.net/problem/10815



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    static int[] cards;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;

        int N = Integer.parseInt(br.readLine());

        cards = new int[N];
        tokenizer = new StringTokenizer(br.readLine(), " ");
        for (int i=0; i<N; i++) {
            cards[i] = Integer.parseInt(tokenizer.nextToken());
        }
        Arrays.sort(cards);

        int M = Integer.parseInt(br.readLine());

        StringBuilder result = new StringBuilder();
        tokenizer = new StringTokenizer(br.readLine(), " ");
        for (int i=0; i<M; i++) {
            result.append(contains(Integer.parseInt(tokenizer.nextToken()))).append(' ');
        }

        System.out.println(result);

    }

    public static int contains(int num) {
        int start = 0;
        int end = cards.length - 1;

        while (start <= end) {
            int mid = (start + end)/2;

            if (cards[mid] == num)
                return 1;
            if (cards[mid] > num)
                end = mid - 1;
            else
                start = mid + 1;
        }
        return 0;
    }
}

```

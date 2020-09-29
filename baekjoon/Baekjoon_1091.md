# [BaekJoon#1091] 카드 섞기



> ### Problem
>
> https://www.acmicpc.net/problem/1091

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token;
        // 3의 배수
        int N = Integer.parseInt(br.readLine());

        // 최종적으로 완성될 수열
        int[] P = new int[N];

        // 섞인 상태
        int[] before = new int[N];

        token = new StringTokenizer(br.readLine(), " ");
        for(int i=0; i<N; i++){
            P[i] = Integer.parseInt(token.nextToken());
            before[i] = i%3;        // 0 1 2 순으로 초기화
        }
        // 카드 섞는 방법
        int[] S = new int[N];
        token = new StringTokenizer(br.readLine(), " ");
        for(int i=0; i<N; i++){
            S[i] = Integer.parseInt(token.nextToken());
        }

        int answer = shuffle(before, P, S);
        System.out.println(answer);
    }

    public static int shuffle(int[] before, int[] finish, int[] pattern){
        int count = 0;

        while(!Arrays.equals(before, finish)){
            int[] after = before.clone();

            for(int i=0; i<pattern.length; i++){
                after[i] = before[pattern[i]];
            }
            before = after;         // 변경값 적용
            count++;
            while(count>120120) return -1;
        }
        return count;
    }
}
```

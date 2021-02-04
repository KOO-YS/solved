# [BaekJoon#2156] 포도주 시식



> ### Problem
>
> https://www.acmicpc.net/problem/2156



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static int[] glass;
    public static int[] drink;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        glass = new int[N+1];
        drink = new int[N+1];

        for(int i=1; i<=N; i++){
            glass[i] = Integer.parseInt(br.readLine());
        }
        if(N == 1){
            System.out.println(glass[1]);
            return;
        }
        drink[1] = glass[1];
        drink[2] = glass[1] + glass[2];
        /**
         * N = 1 or 2
         *      모든 포도주를 마시면 된다
         * N >= 3
         * - 1. N번째 수를 포함하는 경우
         *      - 1.1 N-1번째 포도주도 마시는 경우
         *      ->  N-1번째 포도주 + f(N-3)
         *      - 1.2 N-1번째 포도주를 마시지 않는 경우
         *      ->  f(N-2)
         * - 2. N번째 수를 포함하지 않는 경우
         *      ->  f(N-1)
         */
        System.out.println(maxGlass(N));
    }
    public static int maxGlass(int num){
        if(num>= 3 && drink[num] == 0){        // 아직 초기화되지 않음
            drink[num] = Math.max(
                Math.max(glass[num-1] + maxGlass(num-3), maxGlass(num-2)) + glass[num],
                maxGlass(num-1)
            );
        }
        return drink[num];
    }
}



```

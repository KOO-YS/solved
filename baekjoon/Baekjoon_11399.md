# [BaekJoon#11399] ATM



> ### Problem
>
> https://www.acmicpc.net/problem/11399



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        int[] waiting = new int[N];

        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        for(int i=0; i<N; i++){
            waiting[i] = Integer.parseInt(token.nextToken());
        }
        Arrays.sort(waiting);

        int time = 0;
        for(int i=0; i<N; i++){
            time += waiting[i]*(N-i);
        }
        System.out.println(time);
    }
}

```

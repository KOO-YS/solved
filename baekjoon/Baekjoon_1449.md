# [BaekJoon#1449] 수리공 항승



> ### Problem
>
> https://www.acmicpc.net/problem/1449

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
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        int N = Integer.parseInt(token.nextToken());
        int L = Integer.parseInt(token.nextToken());

        int[] pipe = new int[N];

        token = new StringTokenizer(br.readLine(), " ");

        for (int i=0; i<N; i++) {
            pipe[i] = Integer.parseInt(token.nextToken());
        }

        Arrays.sort(pipe);
        int count = 1;
        int fix = L-1;
        int before = pipe[0];

        for(int i=0; i<N; i++){
            if(pipe[i]-before>fix){
                before = pipe[i];
                count++;
            }
        }

        System.out.println(count);
    }
}
```

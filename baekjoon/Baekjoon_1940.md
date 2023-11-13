# [BaekJoon#1940] 주몽

> ### Problem
>
> https://www.acmicpc.net/problem/1940



> ### Solution

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
        int M = Integer.parseInt(br.readLine());

        int[] arr = new int[N];
        int count = 0;

        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        for (int i=0; i<N; i++) {
            arr[i] = Integer.parseInt(token.nextToken());
        }

        Arrays.sort(arr);

        int front = 0;
        int back = N-1;

        int mix = 0;
        while(front < back) {
            mix = arr[front] + arr[back];
            if (mix == M) {
                count++;
                front++;
                back--;
            }
            else if (mix > M)
                back--;
            else
                front++;
        }
        System.out.println(count);
    }
}

```



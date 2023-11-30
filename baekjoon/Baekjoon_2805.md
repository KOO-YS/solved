# [BaekJoon#2805] 나무 자르기



> ### Problem
>
> https://www.acmicpc.net/problem/2805



> ### Solution

> ```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(tokenizer.nextToken());
        int M = Integer.parseInt(tokenizer.nextToken());

        tokenizer = new StringTokenizer(br.readLine());

        int[] trees = new int[N];
        int sum = 0;
        for (int i=0; i<N; i++) {
            trees[i] = Integer.parseInt(tokenizer.nextToken());
            sum += trees[i];
        }
        System.out.println(getHighest(sum, sum/4, M));

    }
    public static int getHighest(int total, int length, int needs) {
        
//        while ()
        
        
        return 0;
    }
}

>    ```

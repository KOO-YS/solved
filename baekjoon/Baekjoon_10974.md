# [BaekJoon#10974] 모든 순열



> ### Problem
>
> https://www.acmicpc.net/problem/10974



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        int[] output = new int[N];
        boolean[] visited = new boolean[N];
        int[] Nth = new int[N];
        for(int i=0; i<Nth.length; i++){
            Nth[i] = i+1;
        }

        perm(Nth, output, visited, 0, N, N);

    }
    public static void perm(int[] arr, int[] output, boolean[] visited, int depth, int n, int pick){
        if(depth == pick){
            for(int i=0; i<pick; i++){
                System.out.print(output[i]+" ");
            }
            System.out.println();
            return;
        }

        for(int i=0; i<n; i++){
            if(!visited[i]){
                visited[i] = true;
                output[depth] = arr[i];

                perm(arr, output, visited, depth+1, n, pick);
                visited[i] = false;
            }
        }
    }
}

```



> ###### [참고 블로그](//https://bcp0109.tistory.com/13)
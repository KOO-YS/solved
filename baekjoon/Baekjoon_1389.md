# [BaekJoon#1389] 케빈 베이컨의 6단계 법칙



> ### Problem
>
> https://www.acmicpc.net/problem/1389



> ### Solution
>

```java
import java.io.*;
import java.util.*;

class Main {
    public static int N;
    public static int M;
    public static int[][] graphs;
    public static boolean[] isVisited;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");

        N = Integer.parseInt(token.nextToken());
        M = Integer.parseInt(token.nextToken());

        graphs = new int[N+1][N+1];

        while(M-->0){
            token = new StringTokenizer(br.readLine(), " ");
            int num1 = Integer.parseInt(token.nextToken());
            int num2 = Integer.parseInt(token.nextToken());
            graphs[num1][num2]++;
            graphs[num2][num1]++;
        }
        int min = Integer.MAX_VALUE;
        for(int i=1; i<=N; i++){
            for(int j=1; j<=N; j++){
                isVisited = new boolean[N+1];
                if(i == j) continue;

                min = Math.min(min, bfs(i, j));
            }
        }
        System.out.println(min);
    }
    public static int bfs(int A, int B){
        Queue<Integer> queue = new LinkedList<>();
        for(int i=1; i<=N; i++){
            if(graphs[A][i]>0){
                isVisited[i] = true;
                queue.add(i);
            }
        }

        while(!queue.isEmpty()){
            int size = queue.size();
            int count = 1;
            while(size-- >0){
                int temp = queue.poll();

                if(temp == B) return count;

                for(int i=1; i<=N; i++){
                    if(isVisited[i] || graphs[temp][i] == 0) continue;
                    isVisited[i] = true;
                    queue.add(i);
                }
            }
            count++;
        }
        return 0;
    }

}
```

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
    public static int[] way;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");

        N = Integer.parseInt(token.nextToken());
        M = Integer.parseInt(token.nextToken());

        graphs = new int[N+1][N+1];
        way = new int[N+1];
        while(M-->0){
            token = new StringTokenizer(br.readLine(), " ");
            int num1 = Integer.parseInt(token.nextToken());
            int num2 = Integer.parseInt(token.nextToken());
            graphs[num1][num2]++;
            graphs[num2][num1]++;
        }
        int min = Integer.MAX_VALUE;
        int idx = 0;
        for(int i=1; i<=N; i++){
            for(int j=1; j<=N; j++){
                isVisited = new boolean[N+1];
                if(i == j) continue;
                isVisited[i] = true;
                way[i] += bfs(i, j);
            }
        }
        for(int i=1; i<=N; i++){
            if(way[i] < min){
                min = way[i];
                idx = i;
            }
        }
        System.out.println(idx);
    }
    public static int bfs(int A, int B){
        Queue<Integer> queue = new LinkedList<>();
        for(int i=1; i<=N; i++){
            if(graphs[A][i]>0){
                isVisited[i] = true;
                queue.add(i);       // 시작점과 연결된 노드들
            }
        }
        int count = 1;

        while(!queue.isEmpty()){
            int size = queue.size();
            while(size-- >0){
                int temp = queue.poll();        // 연결 노드(temp)로부터 이어서 검색

                if(temp == B) return count;

                for(int i=1; i<=N; i++){
                    if(isVisited[i] || graphs[temp][i] == 0) continue;          // 이미 방문한 노드 || 길이 없는 노드
                    isVisited[i] = true;
                    queue.add(i);       // 연결되는 노드 추가
                }
            }
            count++;
        }
        return 0;
    }

}
```

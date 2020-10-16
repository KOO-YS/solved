# [BaekJoon#1238] 파티



> ### Problem
>
> https://www.acmicpc.net/problem/1238



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static int[] go;
    public static int[] back;

    public static void main(String[] args) throws NumberFormatException, IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());
        int X = Integer.parseInt(token.nextToken());        // 파티가 열릴 마을

        go = new int[N+1];
        back = new int[N+1];

        List<Edge>[] adj = new ArrayList[N+1];
        List<Edge>[] re_adj = new ArrayList[N+1];
        for(int i=1; i<=N; i++){
            go[i] = Integer.MAX_VALUE;
            back[i] = Integer.MAX_VALUE;
            adj[i] = new ArrayList<>();
            re_adj[i] = new ArrayList<>();
        }
        while(M-->0){
            token = new StringTokenizer(br.readLine(), " ");
            int i = Integer.parseInt(token.nextToken());
            int index = Integer.parseInt(token.nextToken());
            int distance = Integer.parseInt(token.nextToken());
            adj[i].add(new Edge(index, distance));
            re_adj[index].add(new Edge(i, distance));

        }
        findWay(go, adj, X);
        findWay(back, re_adj, X);

        int max = 0;
        for(int i=1; i<=N; i++){
            max = Math.max(max, go[i]+back[i]);
        }
        System.out.println(max);


    }
    public static void findWay(int[] arr, List<Edge>[] adj, int X){
        boolean[] visited = new boolean[arr.length];
        arr[X] = 0;
        PriorityQueue<Edge> route = new PriorityQueue<>();
        route.add(new Edge(X, 0));
        while(!route.isEmpty()){
            Edge edge = route.poll();

            if(visited[edge.index]) continue;
            visited[edge.index] = true;

            for(Edge next : adj[edge.index]){
                if(arr[next.index] > edge.distance + next.distance){
                   arr[next.index] = edge.distance + next.distance;
                   route.add(new Edge(next.index, arr[next.index]));
               }
            }
        }
    }
}
class Edge implements Comparable<Edge>{
    int index;
    int distance;

    public Edge(int index, int distance) {
        this.index = index;
        this.distance = distance;
    }

    // for Priority
    @Override
    public int compareTo(Edge o) {
        return this.distance - o.distance;
    }

    @Override
    public String toString() {
        return "index : "+index+", distance : "+distance;
    }
}
```

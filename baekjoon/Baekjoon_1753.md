# [BaekJoon#1753] 최단경로



> ### Problem
>
> https://www.acmicpc.net/problem/1753



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());
        StringBuilder result = new StringBuilder();

        // 정점의 개수 & 간선의 개수
        int V = Integer.parseInt(token.nextToken());
        int E = Integer.parseInt(token.nextToken());

        List<Edge>[] edges = new ArrayList[V+1];
        for(int i=1; i<=V; i++){
            edges[i] = new ArrayList<>();
        }
        int[] shortest = new int[V+1];
        Arrays.fill(shortest, -1);

        // 시작 정점 번호
        int start = Integer.parseInt(br.readLine());
        shortest[start] = 0;        // 자기 자신으로 경로 == 0

        // 간선 입력
        for(int i=0; i<E; i++){
            token = new StringTokenizer(br.readLine(), " ");
            int u = Integer.parseInt(token.nextToken());
            int v = Integer.parseInt(token.nextToken());
            int w = Integer.parseInt(token.nextToken());
            edges[u].add(new Edge(v, w));
        }

        Queue<Edge> queue = new PriorityQueue<>();
        queue.add(new Edge(start, 0));      // 시작점 설정
        while (!queue.isEmpty()){
            Edge now = queue.poll();

            int num = now.num;
            int weight = now.weight;

            for(int i=0; i<edges[num].size(); i++){
                Edge next = edges[num].get(i);

                int nextNum = next.num;
                int nextWeight = next.weight + weight;

                if(shortest[nextNum] == -1 || shortest[nextNum] > nextWeight){
                    shortest[nextNum] = nextWeight;
                    queue.add(new Edge(nextNum, nextWeight));
                }
            }
        }

        for(int i=1; i<=V; i++){
            if(shortest[i]<0) result.append("INF\n");
            else result.append(shortest[i]).append("\n");
        }
        System.out.print(result.toString());
    }
}
class Edge implements Comparable<Edge>{
    int num;
    int weight;

    public Edge(int num, int weight) {
        this.num = num;
        this.weight = weight;
    }

    @Override
    public int compareTo(Edge o) {
        return this.weight - o.weight;
    }
}
```

# [Programmers] 가장 먼 노드

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/49189



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int n, int[][] edge) {
        int answer = 0;

        Graph graph = new Graph(n);
        boolean[] isVisited = new boolean[n+1];

        for(int[] e : edge){
            graph.link(e[0], e[1]);
        }

        bfs(1, isVisited, graph);

        Arrays.sort(graph.nodes);
        int max = graph.nodes[n];
        for(int i=n; i>=0; i--){
            if(max == graph.nodes[i]) answer++;
            else break;
        }

        return answer;
    }
    public void bfs(int start, boolean[] isVisited, Graph graph){
        Queue<Integer> queue = new LinkedList<>();

        queue.add(start);
        graph.nodes[start] = 0;
        isVisited[start] = true;

        while(!queue.isEmpty()){
            int now = queue.poll();
            int depth = graph.nodes[now];
            for(int i : graph.edges[now]){
                if(!isVisited[i]) {         // 아직 방문하지 않았다면
                    graph.nodes[i] = (depth + 1);
                    queue.add(i);
                    isVisited[i] = true;
                }
            }
        }
    }
}
class Graph {
    int[] nodes;
    ArrayList<Integer>[] edges;

    public Graph(int num){
        nodes = new int[num+1];
        edges = new ArrayList[num+1];
        for(int i=1; i<=num; i++){
            edges[i] = new ArrayList<>();
        }
    }
    public void link(int a, int b){
        edges[a].add(b);
        edges[b].add(a);
    }
}

```


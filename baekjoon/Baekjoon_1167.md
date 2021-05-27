# [BaekJoon#1167] 트리의 지름



> ### Problem
>
> https://www.acmicpc.net/problem/1167



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {
    public static int V;
    public static List<int[]>[] linked;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;
        StringBuilder result = new StringBuilder();

        V = Integer.parseInt(br.readLine());

        linked = new ArrayList[V+1];
        for(int i=1; i<=V; i++){
            token = new StringTokenizer(br.readLine());
            int num = Integer.parseInt(token.nextToken());
            linked[num] = new ArrayList<>();

            int linkedNum;
            while((linkedNum = Integer.parseInt(token.nextToken())) != -1){
                // 연결된 정점번호와 그 거리
                linked[num].add(new int[]{linkedNum, Integer.parseInt(token.nextToken())});
            }
        }
        int edge = bfs(1)[0];
        int diameter = bfs(edge)[1];
        System.out.println(diameter);
    }
    public static int[] bfs(int start){
        int max = 0;                // 가장 먼 거리에 존재하는 정점 번호
        int maxDistance = 0;        // 가장 먼 거리

        int[] distance = new int[V+1];      // start에서 각 정점까지의 거리
        // 내림차순으로 정렬
        Queue<int[]> queue = new PriorityQueue<>(new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o2[1] - o1[1];
            }
        });
        boolean[] visited = new boolean[V+1];       // 방문 여부
        
        queue.add(new int[]{start, 0});
        visited[start] = true;

        while(!queue.isEmpty()){
            int now = queue.peek()[0];
            int nowDistance = queue.poll()[1];

            for(int i=0; i<linked[now].size(); i++){
                int next = linked[now].get(i)[0];
                int nextDistance = linked[now].get(i)[1] + nowDistance;
                if(!visited[next]){
                    distance[next] = nextDistance;
                    visited[next] = true;
                    queue.add(new int[]{next, nextDistance});

                    if(nextDistance > maxDistance){ // 최대값 초기화
                        maxDistance = nextDistance;
                        max = next;
                    }
                }
            }
        }
        return new int[]{max, maxDistance};
    }
}
```

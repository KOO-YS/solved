# [BaekJoon#1260] DFS와 BFS



> ### Problem
>
> https://www.acmicpc.net/problem/1260



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.LinkedList;
import java.util.List;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main {

    static List<Integer>[] node;
    static boolean[] visit;
    static StringBuilder result;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());
        int V = Integer.parseInt(token.nextToken());

        node = new ArrayList[N+1];
        visit = new boolean[N+1];
        for (int i=1; i<=N; i++) {
            node[i] = new ArrayList<>();
        }

        while (M-- >0) {
            token = new StringTokenizer(br.readLine());

            int edge1 = Integer.parseInt(token.nextToken());
            int edge2 = Integer.parseInt(token.nextToken());

            node[edge1].add(edge2);
            node[edge2].add(edge1);
        }

        result = new StringBuilder();
        dfs(V);
        System.out.println(result);

        result = new StringBuilder();
        visit = new boolean[N+1];
        bfs(V);
        System.out.println(result);

    }

    private static void dfs(int v) {
        visit[v] = true;
        result.append(v).append(" ");

        Collections.sort(node[v]);
        for (int i : node[v]) {
            if (!visit[i]) {
                visit[i] = true;
                dfs(i);
            }
        }
    }

    private static void bfs(int v) {
        visit[v] = true;
        Queue<Integer> queue = new LinkedList<>();
        queue.add(v);

        int now;
        while (!queue.isEmpty()) {
            now = queue.poll();
            result.append(now).append(" ");
            Collections.sort(node[now]);
            for (int i: node[now]) {
                if (!visit[i]) {
                    visit[i] = true;
                    queue.add(i);
                }
            }

        }
    }
}

```

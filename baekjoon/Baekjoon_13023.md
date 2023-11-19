# [BaekJoon#13023] 친구 관계



> ### Problem
>
> https://www.acmicpc.net/problem/13023



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.StringTokenizer;

public class Main {

    static boolean exist = false;
    static List<Integer>[] node;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());

        node = new ArrayList[N+1];
        for (int i=0; i<N; i++) {
            node[i] = new ArrayList<Integer>();
        }
        boolean[] visit = new boolean[N+1];

        while (M-- > 0) {
            token = new StringTokenizer(br.readLine());

            int a = Integer.parseInt(token.nextToken());
            int b = Integer.parseInt(token.nextToken());

            node[a].add(b);
            node[b].add(a);
        }

        for (int i=0; i<N; i++)
            if (!exist)
                dfs(i, visit, 1);

        System.out.println((exist)? 1:0);
    }

    static void dfs(int i, boolean[] visit, int depth) {
        if (depth ==5) {
            exist = true;
            return;
        }
        visit[i] = true;
        for (int n : node[i]) {
            if (!visit[n]) {
                dfs(n, visit, depth + 1);
            }
        }
        visit[i] = false;

    }
}
```


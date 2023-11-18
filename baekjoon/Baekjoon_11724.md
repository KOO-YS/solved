# [BaekJoon#11724] 연결 요소의 개수



> ### Problem
>
> https://www.acmicpc.net/problem/11724



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.StringTokenizer;

public class Main {

    static boolean[] visit;
    static List<Integer>[] node;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());

        node = new ArrayList[N+1];
        visit = new boolean[N+1];
        for (int i=1; i<=N; i++) {
            node[i] = new ArrayList<Integer>();
        }

        int num1, num2;
        while (M-- > 0){
            token = new StringTokenizer(br.readLine());
            num1 = Integer.parseInt(token.nextToken());
            num2 = Integer.parseInt(token.nextToken());

            node[num1].add(num2);
            node[num2].add(num1);
        }

        int count = 0;
        for (int i=1; i<=N; i++) {
            if (!visit[i]) {
                count ++;
                dfs(i);
            }
        }
        System.out.println(count);

    }
    public static void dfs(int i) {
        visit[i] = true;
        for (int n : node[i]) {
            if (!visit[n])
                dfs(n);
        }
    }
}
```

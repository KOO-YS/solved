# [BaekJoon#14496] 그대, 그머가 되어



> ### Problem
>
> https://www.acmicpc.net/problem/14496



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());
        StringBuilder result = new StringBuilder();

        int a = Integer.parseInt(token.nextToken());
        int b = Integer.parseInt(token.nextToken());

        token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());

        List<Integer>[] convert = new ArrayList[N+1];
        for(int i=0; i<convert.length; i++){
            convert[i] = new ArrayList<>();
        }

        int[] min = new int[N+1];
        Arrays.fill(min, -1);

        while(M-- > 0){
            token = new StringTokenizer(br.readLine());

            int c1 = Integer.parseInt(token.nextToken());
            int c2 = Integer.parseInt(token.nextToken());

            convert[c1].add(c2);
            convert[c2].add(c1);
        }

        Queue<Integer> queue = new PriorityQueue<>();
        // 시작점
        queue.add(a);
        min[a] = 0;     // 시작 횟수 초기화
        while (!queue.isEmpty()){
            int now = queue.poll();
            for(int i=0; i<convert[now].size(); i++){
                int next = convert[now].get(i);

                if(min[next] == -1 || min[next] > min[now]+1){      // 더 작은 값이 등장
                    min[next] = min[now] + 1;
                    queue.add(next);
                }
            }
        }
        System.out.println(min[b]);
    }
}
```




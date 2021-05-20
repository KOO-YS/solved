# [BaekJoon#18352] 특정 거리의 도시 찾기



> ### Problem
>
> https://www.acmicpc.net/problem/18352



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());
        int K = Integer.parseInt(token.nextToken());
        int X = Integer.parseInt(token.nextToken());

        int[] distance = new int[N+1];
        Arrays.fill(distance, -1);
        distance[X] = 0;

        List<Integer>[] linked = new ArrayList[N+1];
        for(int i=1; i<=N; i++){
            linked[i] = new ArrayList<>();
        }

        while(M-- > 0){
            token = new StringTokenizer(br.readLine());
            linked[Integer.parseInt(token.nextToken())].add(Integer.parseInt(token.nextToken()));
        }
        Queue<Integer> queue = new PriorityQueue<>();
        queue.add(X);       // 시작점

        while(!queue.isEmpty()){
            int now = queue.poll();

            for(int i=0; i<linked[now].size(); i++){
                int next = linked[now].get(i);

                if(distance[next] == -1 || distance[next] > distance[now]+1) {
                    distance[next] = distance[now] + 1;
                    queue.add(next);
                }
            }
        }
        for(int i=1; i<distance.length; i++){
            if(distance[i] == K) result.append(i).append("\n");
        }
        if(result.toString().equals("")) System.out.print("-1");
        else System.out.print(result.toString());
    }
}

```

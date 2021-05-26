# [BaekJoon#1176] 트리의 지름



> ### Problem
>
> https://www.acmicpc.net/problem/1176



> ### Solution
>
> ```java
> import java.io.*;
> import java.util.*;
> 
> //https://www.acmicpc.net/problem/1167
>    class Main {
>        public static void main(String[] args) throws Exception {
>            BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
>            StringTokenizer token;
>         StringBuilder result = new StringBuilder();
>    
>            int V = Integer.parseInt(br.readLine());
> 
>            int[] distance = new int[V+1];
>            List<int[]>[] linked = new ArrayList[V+1];
>            for(int i=1; i<=V; i++){
>                token = new StringTokenizer(br.readLine());
>                int num = Integer.parseInt(token.nextToken());
>                linked[num] = new ArrayList<>();
> 
>                int linkedNum;
>                while((linkedNum = Integer.parseInt(token.nextToken())) != -1){
>                    // 연결된 정점번호와 그 거리
>                    linked[num].add(new int[]{linkedNum, Integer.parseInt(token.nextToken())});
>                }
>            }
>    
>            Queue<Integer> queue = new LinkedList<>();
>         boolean[] visited = new boolean[V+1];
>            queue.add(1);
>         visited[1] = true;
>            while(!queue.isEmpty()){
>                int now = queue.poll();
>                for(int i=0; i<linked[i].size(); i++){
>    
>                }
>            }
>    
>        }
>    }
>    
>    ```



>#### 풀이
>
>임의의 점에서 시작했을 때 가장 먼거리의 점이 존재 -> 지름의 한쪽 끝점
>
>끝점에서 가장 먼 점을 찾아 거리 확인 -> 지름

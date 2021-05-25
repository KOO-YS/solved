# [BaekJoon#1916] 최소비용 구하기



> ### Problem
>
> https://www.acmicpc.net/problem/1916



> ### Solution
>
> ```java
> import java.io.*;
> import java.util.*;
> 
> class Main {
>     public static void main(String[] args) throws Exception {
>         BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
>         StringTokenizer token;
>         StringBuilder result = new StringBuilder();
> 
>         int N = Integer.parseInt(br.readLine());
>         int M = Integer.parseInt(br.readLine());
> 
>         int[] min = new int[N+1];
>         Arrays.fill(min, -1);
>         List<int[]>[] linked = new ArrayList[N+1];
>         for(int i=1; i<=N; i++){
>             linked[i] = new ArrayList<>();
>         }
> 
>         while(M-- > 0){
>             token = new StringTokenizer(br.readLine());
>             // linked[depart].add(arrival, distance);
>             linked[Integer.parseInt(token.nextToken())].add(new int[]{Integer.parseInt(token.nextToken()), Integer.parseInt(token.nextToken())});
>         }
>         token = new StringTokenizer(br.readLine());
>         int depart = Integer.parseInt(token.nextToken());
>         int arrival = Integer.parseInt(token.nextToken());
> 
>         int answer = getShortest(depart, arrival, min, linked);
> 
>         System.out.println(answer);
>     }
>     public static int getShortest(int depart, int arrival, int[] min, List<int[]>[] linked){
>         Queue<int[]> queue = new PriorityQueue<>(new Comparator<int[]>() {
>             // 거리 오름차순
>             @Override
>             public int compare(int[] o1, int[] o2) {
>                 return o1[1] - o2[1];
>             }
>         });
>         min[depart] = 0;
>         queue.add(new int[]{depart, 0});
> 
>         while (!queue.isEmpty()){
>             int[] now = queue.poll();
>             int nowDepart = now[0];
>             int nowDistance = now[1];
> 
>             for(int i=0; i<linked[nowDepart].size(); i++){
>                 int[] next = linked[nowDepart].get(i);
>                 int nextDepart = next[0];
>                 int nextDistance = next[1] + nowDistance;
> 
>                 if(min[nextDepart] == -1 || min[nextDepart] > nextDistance){
>                     min[nextDepart] = nextDistance;
>                     queue.add(new int[]{nextDepart, min[nextDepart]});
>                 }
>             }
>         }
>         return min[arrival];
>     }
> }
> ```
>


# [BaekJoon#1697] 숨바꼭질



> ### Problem
>
> https://www.acmicpc.net/problem/1697



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main {
    public static int[] depth;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int K = Integer.parseInt(token.nextToken());

        if(N == K){
            System.out.println(0);
            return;
        }

        bfs(N, K);
    }
    public static void bfs(int N, int K){
        depth = new int[100001];

        // init
        Queue<Integer> queue = new LinkedList<>();
        queue.add(N);
        depth[N] = 1;

        // BFS
        while (!queue.isEmpty()){
            int now = queue.poll();
            int temp;
            for(int i=0; i<3; i++){
                temp = move(now, i);
                // condition: 아직 방문하지 않음 && 범위 내 포함
                if(isBoundary(temp) && depth[temp] == 0){
                    if(temp == K){
                        System.out.println(depth[now]);
                        return;
                    }
                    queue.add(temp);
                    depth[temp] = depth[now]+1;
                }
            }
        }
    }
    // 가능한 이동 경로
    public static int move(int num, int way){
        switch (way){
            case 0:
                return num+1;
            case 1:
                return num-1;
            case 2:
                return 2*num;
            default:
                return 0;
        }
    }
    // 범위 확인
    public static boolean isBoundary(int num){
        if(num < 0) return false;       // 주의 : 0도 가능
        if(num > 100000) return false;

        return true;
    }
}
```



> 0도 가능한 범위였다...☆
>
> 범위 잘 생각하긔..

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Main {
    public static boolean[] isVisited;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int K = Integer.parseInt(token.nextToken());

        isVisited = new boolean[100001];

        if(N == K) {
            System.out.println(0);
            return;
        }

        int count = 0;
        Queue<Integer> queue = new LinkedList<>();
        isVisited[N] = true;
        queue.add(N);

        while(!queue.isEmpty()){
            int length = queue.size();
            for(int i=0; i<length; i++){

                int now = queue.poll();

                if(now == K){
                    System.out.println(count);
                    return;
                }
                if((now-1)>=0 && !isVisited[now-1]){
                    queue.add(now-1);
                    isVisited[now-1] = true;
                }
                if((now+1)<100001 && !isVisited[now+1]){
                    queue.add(now+1);
                    isVisited[now+1] = true;
                }
                if((now*2)<100001 && !isVisited[now*2]){
                    queue.add(now*2);
                    isVisited[now*2] = true;
                }
            }
            count++;
        }
    }
}
```


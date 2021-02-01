# [BaekJoon#1697] 숨바꼭질



> ### Problem
>
> https://www.acmicpc.net/problem/1697



> ### Solution (실패)
>

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
                if((now-1)>0 && !isVisited[now-1]){
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

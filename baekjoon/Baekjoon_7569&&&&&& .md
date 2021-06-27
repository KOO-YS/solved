# [BaekJoon#7569] 토마토



> ### Problem
>
> https://www.acmicpc.net/problem/7569



> ### Solution

```java
```

<br>



> ### 오답 -> 시간초과

```java
import java.io.*;
import java.util.*;

class Main {
//https://www.acmicpc.net/problem/7569
    public static int[][][] box;
    public static boolean[][][] visited;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;

        token= new StringTokenizer(br.readLine());

        int M = Integer.parseInt(token.nextToken());    // 가로 칸 수
        int N = Integer.parseInt(token.nextToken());    // 세로 칸 수
        int H = Integer.parseInt(token.nextToken());    // 높이

        box = new int[H][N][M];
        visited = new boolean[H][N][M];

        for(int h=0; h<H; h++){
            for(int n=0; n<N; n++){
                token = new StringTokenizer(br.readLine());
                for(int m=0; m<M; m++){
                    box[h][n][m] = Integer.parseInt(token.nextToken());
                }
            }
        }

        for(int h=0; h<H; h++){
            for(int n=0; n<N; n++){
                for(int m=0; m<M; m++){
                    if(box[h][n][m] == 1 && !visited[h][n][m]) ripe(new Dot(n, m, h), 1);
                }
            }
        }
        if(!check()){
            System.out.println(-1);
            return;
        }
        System.out.println(print()-1);
    }

    public static void ripe(Dot now, int level){
        visited[now.z][now.x][now.y] = true;

        for(int i=0; i<6; i++){
            Dot next = new Dot(now.x+dx[i], now.y+dy[i], now.z+dz[i]);

            if(isBoundary(next.x, next.y, next.z)){
                if(
                // 방문했지만 더 빠르게 익을 가능성이 있다면
                (visited[next.z][next.x][next.y] && box[next.z][next.x][next.y] > level+1)
                ||
                // 아직 방문한 적 없는 덜익은 토마토라면
                (!visited[next.z][next.x][next.y] && box[next.z][next.x][next.y] == 0))
                {
                    box[next.z][next.x][next.y] = level+1;
                    ripe(next, level+1);
                }
            }

        }
    }

    public static boolean isBoundary(int x, int y, int z){
        if(z < 0 || z >= box.length) return false;
        if(x < 0 || x >= box[0].length) return false;
        if(y < 0 || y >= box[0][0].length) return false;

        return true;
    }
    public static int[] dz = {0, 0, 0, 0, -1, 1};
    public static int[] dx = {-1, 0, 1, 0, 0, 0};
    public static int[] dy = {0, 1, 0, -1, 0, 0};

    public static int print(){
        int max = 0;
        for(int[][] b : box){
            for(int[] i : b) {
                Arrays.sort(i);
                max = Math.max(max, i[i.length-1]);
            }
        }
        return max;
    }

    public static boolean check(){
        for(int[][] line : box){
            for(int[] arr : line) {
                for (int a : arr) if(a == 0) return false;
            }
        }
        return true;
    }

}
class Dot{
    int x;
    int y;
    int z;

    public Dot(int x, int y, int z) {
        this.x = x;
        this.y = y;
        this.z = z;
    }
}

```

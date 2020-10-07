# [BaekJoon#2178] 미로 탐색



> ### Problem
>
> https://www.acmicpc.net/problem/2178

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());

        maze = new int[N][M];

        for(int i=0; i<N; i++){
            char[] temp = br.readLine().toCharArray();
            for(int j=0; j<M; j++){
                maze[i][j] = temp[j]-48;
            }
        }
        // 도착지점 초기화
        endX = N-1;
        endY = M-1;

        int answer = findWay(0, 0);
        System.out.println(answer);
    }

    public static int[][] maze;

    public static int endX;
    public static int endY;

    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};

    public static int findWay(int x, int y){
        int count = 0;
        Queue<Location> queue = new LinkedList<>();
        queue.add(new Location(x, y));

        while(!queue.isEmpty()){
            Location now = queue.poll();
            count = maze[now.x][now.y];

            for(int d=0; d<4; d++){
                int tempX = now.x + dx[d];
                int tempY = now.y + dy[d];

                if(isBoundary(tempX, tempY) && maze[tempX][tempY] == 1){
                    maze[tempX][tempY] = count+1;
                    if(tempX == endX && tempY == endY) return maze[tempX][tempY];
                    queue.add(new Location(tempX, tempY));
                }
            }
        }
        return count;
    }
    public static boolean isBoundary(int x, int y){
        if(x < 0 || y < 0 || x >= maze.length || y >= maze[0].length) return false;
        return true;
    }
}
class Location{
    int x;
    int y;

    public Location(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

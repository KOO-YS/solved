# [BaekJoon#7576] 토마토



> ### Problem
>
> https://www.acmicpc.net/problem/7576



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");

        int M = Integer.parseInt(token.nextToken());
        int N = Integer.parseInt(token.nextToken());

        Queue<Location> queue = new LinkedList<>();
        // init
        int[][] box = new int[N][M];
        for(int i=0; i<N; i++){
            token = new StringTokenizer(br.readLine(), " ");
            for(int j=0; j<M; j++){
                int index = Integer.parseInt(token.nextToken());
                if(index == 1) queue.add(new Location(i,j));
                box[i][j] = index;
            }
        }
        int answer = ripeTomato(box, queue);
        System.out.println(answer);

    }
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};
    public static int ripeTomato(int[][] box, Queue<Location> queue){
        int days = 0;
        while(!queue.isEmpty()){
            Location tomato = queue.poll();
            days = tomato.days;
            for(int i=0; i<4; i++){
                int nearX = tomato.x + dx[i];
                int nearY = tomato.y + dy[i];
                if(!isBoundary(box, nearX, nearY)) continue;

                if(box[nearX][nearY] == 0){
                    box[nearX][nearY] = 1;
                    queue.add(new Location(nearX, nearY, days+1));
                }
            }
        }
        if(checkTomato(box)) return days;
        return -1;
    }
    public static boolean isBoundary(int[][] box, int x, int y){
        if(0<=x && 0<=y && x<box.length && y<box[0].length) return true;
        return false;
    }
    public static boolean checkTomato(int[][] box){
        for(int i=0; i<box.length; i++){
            for(int j=0; j<box[i].length; j++){
                if(box[i][j] == 0) return false;
            }
        }
        return true;
    }
}
class Location{
    int x;
    int y;
    int days;

    public Location(int x, int y) {
        this.x = x;
        this.y = y;
        this.days = 0;
    }

    public Location(int x, int y, int days) {
        this.x = x;
        this.y = y;
        this.days = days;
    }
}
```


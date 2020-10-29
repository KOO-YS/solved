## [BaekJoon#2638] 치즈



> ### Problem
>
> https://www.acmicpc.net/problem/2638



> ### Solution
>

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(token.nextToken());
        int M = Integer.parseInt(token.nextToken());

        int[][] cheese = new int[N][M];
        // setting
        for(int i=0; i<N; i++){
            token = new StringTokenizer(br.readLine());
            for(int j=0; j<M; j++){
                cheese[i][j] = Integer.parseInt(token.nextToken());
            }
        }

        int days = melt(cheese);
        System.out.println(days);
    }

    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};

    public static int melt(int[][] cheese){
        int days = 0;

        while(true) {
            boolean[][] visited = new boolean[cheese.length][cheese[0].length];
            int[][] count = new int[cheese.length][cheese[0].length];

            Queue<Location> queue = new LinkedList<>();

            queue.add(new Location(0, 0));
            while (!queue.isEmpty()) {
                Location now = queue.poll();

                if (visited[now.x][now.y]) continue;     // 이미 방문
                visited[now.x][now.y] = true;

                for (int i = 0; i < 4; i++) {
                    int tempX = now.x + dx[i];
                    int tempY = now.y + dy[i];

                    if (!isBoundary(tempX, tempY, cheese)) continue;

                    if (cheese[tempX][tempY] == 1) count[tempX][tempY]++;
                    else if (!visited[tempX][tempY]) queue.add(new Location(tempX, tempY));
                }
            }
            
            boolean fail = true;
            for (int i = 0; i < count.length; i++) {
                for (int j = 0; j < count[0].length; j++) {
                    if(count[i][j] >= 2){
                        fail = false;
                        cheese[i][j] = 0;
                    }
                }
            }
            if(!fail) days++;
            else break;
        }
        return days;
    }
    public static boolean isBoundary(int x, int y, int[][] arr){
        if(x >= 0 && x < arr.length && y >= 0 && y < arr[0].length) return true;
        return false;
    }
}
class Location {
    int x;
    int y;

    public Location(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

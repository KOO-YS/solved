# [BaekJoon#14940] 쉬운 최단거리



> ### Problem
>
> https://www.acmicpc.net/problem/14940




> ### Solution 

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

// https://www.acmicpc.net/problem/14226
public class Main {
    public static int n;
    public static int m;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        n = Integer.parseInt(tokenizer.nextToken());
        m = Integer.parseInt(tokenizer.nextToken());

        map = new int[n][m];
        result = new int[n][m];
        visited = new boolean[n][m];
        int startX = 0, startY = 0, num;

        for (int i=0; i<n; i++) {
            tokenizer = new StringTokenizer(br.readLine());
            for (int j=0; j<m; j++) {
                num = Integer.parseInt(tokenizer.nextToken());
                map[i][j] = num;
                if (num == 2) {
                    startX = i;
                    startY = j;
                }
            }
        }

        bfs(startX, startY);

        StringBuilder answer = new StringBuilder();
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                if(!visited[i][j] && map[i][j] == 1) answer.append(-1);
                else answer.append(result[i][j]);
                answer.append(' ');
            }
            answer.append('\n');
        }
        System.out.print(answer.toString());
    }

    public static int[][] map;
    public static int[][] result;
    public static boolean[][] visited;

    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};

    public static boolean isBoundary(int x, int y) {
        if (x < 0 || x >= n) return false;
        if (y < 0 || y >= n) return false;
        return true;
    }

    public static void bfs(int x, int y) {
        Queue<Point> queue = new PriorityQueue<>();
        queue.add(new Point(x, y));

        while (!queue.isEmpty()) {
            Point now = queue.poll();
            int d = now.distance;

            int nextX = 0, nextY = 0;
            for (int i=0; i<4; i++) {
                nextX = now.x + dx[i];
                nextY = now.y + dy[i];

                if (!isBoundary(nextX, nextY)) continue;
                if (!visited[nextX][nextY] && map[nextX][nextY] == 1) {
                    queue.add(new Point(nextX, nextY, d+1));
                    result[nextX][nextY] = d+1;
                    visited[nextX][nextY] = true;
                }
            }
        }
    }
}

class Point implements Comparable<Point>{

    int x;
    int y;
    int distance;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
        this.distance = 0;
    }

    public Point(int x, int y, int distance) {
        this.x = x;
        this.y = y;
        this.distance = distance;
    }

    @Override
    public int compareTo(Point o) {
        return this.distance - o.distance;
    }
}
```

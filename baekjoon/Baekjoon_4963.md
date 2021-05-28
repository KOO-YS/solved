# [BaekJoon#4963] 



> ### Problem
>
> https://www.acmicpc.net/problem/4963



> ### Solution

```java
import java.io.*;
import java.util.*;

// https://www.acmicpc.net/problem/4963
class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;
        StringBuilder result = new StringBuilder();

        String testCase;
        while(!(testCase =  br.readLine()).equals("0 0")){
            token = new StringTokenizer(testCase);
            int w = Integer.parseInt(token.nextToken());
            int h = Integer.parseInt(token.nextToken());

            int[][] map = new int[h][w];
            // 지도 초기화
            for(int i=0; i<h; i++){
                token = new StringTokenizer(br.readLine());
                for(int j=0; j<w; j++){
                    // 1 : 땅 or 0 : 바다
                    map[i][j] = Integer.parseInt(token.nextToken());
                }
            }
            int count = getLandCount(w, h, map);
            result.append(count).append("\n");
        }
        System.out.print(result.toString());
    }
    // 가로, 대각선, 세로, 역대각선
    public static int[] dx = {0, 1, 1, 1};
    public static int[] dy = {1, 1, 0, -1};

    public static int getLandCount(int w, int h, int[][] map) {
        int count = 0;
        boolean[][] visited = new boolean[h][w];
        Queue<int[]> queue;
        for(int i=0; i<h; i++){
            for(int j=0; j<w; j++){
                if(!visited[i][j] && map[i][j] == 1){       // 방문하지 않은 땅
                    count ++;
                    queue = new LinkedList<>();
                    queue.add(new int[]{i, j});     // start
                    visited[i][j] = true;

                    while(!queue.isEmpty()) {
                        int[] next = queue.poll();
                        int nextX, nextY;
                        for (int k = 0; k < 3; k++) {
                            nextX = next[0] + dx[k];
                            nextY = next[1] + dy[k];

                            if(isBoundary(h, w, nextX, nextY)) {

                                if (!visited[nextX][nextY] && map[nextX][nextY] == 1) {
                                    queue.add(new int[]{nextX, nextY});
                                    visited[nextX][nextY] = true;
                                }
                            }
                        }
                    }

                }

            }
        }
        return count;
    }

    public static boolean isBoundary(int h, int w, int nextX, int nextY) {
        if(nextX < 0 || nextX >= h) return false;
        else if(nextY < 0 || nextY >= w) return false;
        return true;
    }
}
```

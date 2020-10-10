# [BaekJoon#1012] 유기농 배추



> ### Problem
>
> https://www.acmicpc.net/problem/1012



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
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;
        StringBuilder result = new StringBuilder();

        int T = Integer.parseInt(br.readLine());
        while(T-->0){
            token = new StringTokenizer(br.readLine(), " ");

            int N = Integer.parseInt(token.nextToken());
            int M = Integer.parseInt(token.nextToken());
            int K = Integer.parseInt(token.nextToken());

            int[][] field = new int[N][M];

            while(K-->0){
                token = new StringTokenizer(br.readLine(), " ");

                field[Integer.parseInt(token.nextToken())][Integer.parseInt(token.nextToken())] = 1;
            }
            int answer = checkCabbage(field);
            result.append(answer+"\n");
        }
        System.out.print(result.toString());
    }
    public static int checkCabbage(int[][] field){
        int count = 0;

        for(int i=0; i<field.length; i++){
            for(int j=0; j<field[0].length; j++){
                if(field[i][j] == 1) {
                    bfs(field, i, j);
                    count++;
                }
            }
        }
        return count;
    }
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};
    public static void bfs(int[][] field, int x, int y){
        Queue<int[]> queue = new LinkedList<>();
        queue.add(new int[]{x,y});
        field[x][y] = 0;        // finish checking

        while(!queue.isEmpty()) {
            int[] location = queue.poll();
            for (int d = 0; d < 4; d++) {
                int tempX = location[0] + dx[d];
                int tempY = location[1] + dy[d];

                if(isBoundary(field, tempX, tempY) && field[tempX][tempY] == 1){
                    field[tempX][tempY] = 0;
                    queue.add(new int[]{tempX, tempY});
                }
            }
        }

    }
    public static boolean isBoundary(int[][] arr, int x, int y){
        if(x < 0 || y < 0 || x >= arr.length || y >= arr[0].length) return false;
        return true;
    }
}
```

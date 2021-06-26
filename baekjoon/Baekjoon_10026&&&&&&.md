# [BaekJoon#10026] 적록색약



> ### Problem
>
> https://www.acmicpc.net/problem/10026



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {

    public static char[][] map;
    public static boolean[][] visited;
    public static int count;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String result;
        int N = Integer.parseInt(br.readLine());

        count = 0;
        map = new char[N][N];
        visited = new boolean[N][N];

        // initialize
        for(int i=0; i<N; i++){
            map[i] = br.readLine().toCharArray();
        }

        for(int i=0; i<N; i++) {
            for(int j=0; j<N; j++) {
                if(!visited[i][j]) getArea(i, j, map[i][j]);
            }
        }
        result = count+" ";

        count = 0;
        visited = new boolean[N][N];

        for(int i=0; i<N; i++){
            for(int j=0; j<N; j++){
                if(map[i][j] == 'G') map[i][j] = 'R';
            }
        }
        for(int i=0; i<N; i++) {
            for(int j=0; j<N; j++) {
                if(!visited[i][j]) getArea(i, j, map[i][j]);
            }
        }

        System.out.print(result+count);

    }

    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};
    public static void getArea(int x, int y, char ch){
        Queue<int[]> queue = new LinkedList<>();

        queue.add(new int[]{x, y});
        visited[x][y] = true;

        while(!queue.isEmpty()){
            int[] now = queue.poll();
            int nowX = now[0];
            int nowY = now[1];

            for(int i=0; i<4; i++){
                int nextX = nowX + dx[i];
                int nextY = nowY + dy[i];

                if(isBoundary(nextX, nextY)) {
                    if(!visited[nextX][nextY] && map[nextX][nextY] == ch){
                        queue.add(new int[]{nextX, nextY});
                        visited[nextX][nextY] = true;
                    }
                }
            }
        }
        count++;
    }

    public static boolean isBoundary(int x, int y){
        if(x < 0 || x >= map.length) return false;
        if(y < 0 || y >= map.length) return false;

        return true;
    }
    
	// 차이를 enum 아니면 상수로 둔다면?
    public static final int BLUE = 0;
    public static final int RED = 1;
    public static final int GREEN = 2;

    /*
    * R, G, B
    * 구역 -> 같은 색 (상,하,좌,우)
    *
    * 적록색약 X -> R | G | B
    * 적록색약 O -> (R , G) | B
    * */
//    public static int area(){
//
//    }


}


```
<br>


> ### Solution (before)

```java
import java.io.*;
import java.util.*;

class Main {

    public static char[][] map;
    public static boolean[][] visited;
    public static int count;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String result;
        int N = Integer.parseInt(br.readLine());

        count = 0;
        map = new char[N][N];
        visited = new boolean[N][N];

        // initialize
        for(int i=0; i<N; i++){
            map[i] = br.readLine().toCharArray();
        }

        for(int i=0; i<N; i++) {
            for(int j=0; j<N; j++) {
                if(!visited[i][j]) getArea(i, j, map[i][j]);
            }
        }
        result = count+" ";

        count = 0;
        visited = new boolean[N][N];

        for(int i=0; i<N; i++){
            for(int j=0; j<N; j++){
                if(map[i][j] == 'G') map[i][j] = 'R';
            }
        }
        for(int i=0; i<N; i++) {
            for(int j=0; j<N; j++) {
                if(!visited[i][j]) getArea(i, j, map[i][j]);
            }
        }

        System.out.print(result+count);

    }

    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};
    public static void getArea(int x, int y, char ch){
        Queue<int[]> queue = new LinkedList<>();

        queue.add(new int[]{x, y});
        visited[x][y] = true;

        while(!queue.isEmpty()){
            int[] now = queue.poll();
            int nowX = now[0];
            int nowY = now[1];

            for(int i=0; i<4; i++){
                int nextX = nowX + dx[i];
                int nextY = nowY + dy[i];

                if(isBoundary(nextX, nextY)) {
                    if(!visited[nextX][nextY] && map[nextX][nextY] == ch){
                        queue.add(new int[]{nextX, nextY});
                        visited[nextX][nextY] = true;
                    }
                }
            }
        }
        count++;
    }

    public static boolean isBoundary(int x, int y){
        if(x < 0 || x >= map.length) return false;
        if(y < 0 || y >= map.length) return false;

        return true;
    }
}
```

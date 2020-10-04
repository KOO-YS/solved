# [BaekJoon#2146] 다리 만들기



> ### Problem
>
> https://www.acmicpc.net/problem/2146



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {

    public static int[][] map;
    public static int N;
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};
    public static int islandNum = 1;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        N = Integer.parseInt(br.readLine());
        map = new int[N][N];
        StringTokenizer token;

        for(int i=0; i<N; i++){
            token = new StringTokenizer(br.readLine(), " ");
            for(int j=0; j<N; j++){
                map[i][j] = Integer.parseInt(token.nextToken());
            }
        }
        identifyIsland();

        List<Integer> paths = new ArrayList<>();
        for(int i=0; i<N; i++){
            for(int j=0; j<N; j++){
                if(map[i][j] != 0 ){
                    int[][] temp = copyArr(map);
                    paths.add(findShortestPath(temp, i, j));
                }
            }
        }
        Collections.sort(paths);
        System.out.println(paths.get(0));       // 정렬 후 가장 작은 값
    }
    // 가장 짧은 경로 찾기
    public static int findShortestPath(int[][] temp, int i, int j){
        int min = 1001;
        Queue<Location> queue = new LinkedList<>();
        queue.add(new Location(i, j));

        while(!queue.isEmpty()){

            Location now = queue.poll();

            for(int d=0; d<4; d++){
                int nearX = now.x + dx[d];
                int nearY = now.y + dy[d];

                if(nearX < 0 || nearY < 0 || nearX >= N || nearY >= N) continue;
                if(temp[nearX][nearY] == -1) continue;
                if(temp[nearX][nearY] == map[i][j]) continue;

                if(temp[nearX][nearY] != 0) {
                    return Math.min(now.distance, min);
                }
                queue.add(new Location(nearX, nearY, (now.distance+1)));
                temp[nearX][nearY] = -1;
            }
        }
        return min;
    }
    // 섬끼리 구분
    public static void identifyIsland(){
        for(int i=0; i<N; i++){
            for(int j=0; j<N; j++){
                if(map[i][j] == 1){
                    map[i][j] = ++islandNum;
                    dfs(i, j);
                }
            }
        }
    }

    // 섬 구분을 위한 깊이 우선 탐색
    public static void dfs(int i, int j){
        for(int d=0; d<4; d++){
            int nearX = i+dx[d];
            int nearY = j+dy[d];

            if(nearX < 0 || nearY < 0 || nearX >= N || nearY >= N) continue;
            if(map[nearX][nearY] == islandNum) continue;
            if(map[nearX][nearY] == 0) continue;

            if(map[nearX][nearY] == 1){
                map[nearX][nearY] = islandNum;
                dfs(nearX, nearY);
            }
        }
    }
    // 복사
    public static int[][] copyArr(int[][] from){
        int[][] to = new int[from.length][from[0].length];
        for(int i=0; i<from.length; i++){
            for(int j=0; j<from[i].length; j++){
                to[i][j] = from[i][j];
            }
        }
        return to;
    }
}

class Location{
    int x;
    int y;
    int distance;

    public Location(int x, int y) {
        this.x = x;
        this.y = y;
        this.distance = 0;
    }

    public Location(int x, int y, int distance) {
        this.x = x;
        this.y = y;
        this.distance = distance;
    }
}
```





메모리가 엄청남.... 

나중에 참고하기..

https://zoonvivor.tistory.com/122
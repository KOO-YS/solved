# [Programmers] 카카오프렌즈 컬러링북



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/1829



> ### Solution (실패) 
>
> 참고 : https://swycha.tistory.com/141

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public int[] solution(int m, int n, int[][] picture) {
        int numberOfArea = 0;
        int maxSizeOfOneArea = 1;


        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(picture[i][j] > 0) {
                    numberOfArea++;
                    maxSizeOfOneArea = Math.max(maxSizeOfOneArea, bfs(picture, i, j));
                }
            }
        }


        int[] answer = new int[2];
        answer[0] = numberOfArea;
        answer[1] = maxSizeOfOneArea;
        return answer;
    }
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};
    public static int bfs(int[][] picture, int x, int y){
        Queue<Location> queue = new LinkedList<>();
        int value = picture[x][y];
        int size = 1;
        picture[x][y] = 0;
        queue.add(new Location(x, y));

        int tempX, tempY;
        while(!queue.isEmpty()){
            Location now = queue.poll();
            for(int i=0; i<4; i++){
                    tempX = now.x + dx[i];
                    tempY = now.y + dy[i];

                    if(!isBoundary(picture, tempX, tempY)) continue;
                    if(picture[tempX][tempY] == value){
                        queue.add(new Location(tempX, tempY));
                        picture[tempX][tempY] = 0;
                        size++;

                    }
            }
        }
        return size;
    }
    public static boolean isBoundary(int[][] picture, int x, int y){
        if(x >= 0 && x < picture.length && y >= 0 && y < picture[0].length) return true;
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


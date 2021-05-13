# [Programmers] 행렬 테두리 회전하기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/77485

<br>

> ### solution

```java
import java.util.*;

class Solution {
    public int[] solution(int rows, int columns, int[][] queries) {
        int[] answer = new int[queries.length];
        int index = 0;  // 회전 인덱스

        arr = new int[rows][columns];

        // initialize
        int count = 1;
        for(int i=0; i<rows; i++){
            for(int j=0; j<columns; j++){
                arr[i][j] = count++;
            }
        }

        for(int i=0; i<queries.length; i++){
            circle(queries[i][0]-1, queries[i][1]-1, queries[i][2]-1, queries[i][3]-1);
            answer[index] = getMin(queries[i][0]-1, queries[i][1]-1, queries[i][2]-1, queries[i][3]-1);
            index++;
        }

        return answer;
    }
    public int[][] arr;
    /*
    * 테두리 회전
    * */
    public void circle(int startX, int startY, int endX, int endY){
        int next = 0;
        int before = 0;

        // 왼 -> 오
        next = arr[startX][endY];
        for(int i = endY; i>startY; i--){
            arr[startX][i] = arr[startX][i- 1];
        }

        // 위 -> 아래
        before = next;
        next = arr[endX][endY];
        for(int i = endX; i>startX+1; i--){
            arr[i][endY] = arr[i-1][endY];
        }
        arr[startX+1][endY] = before;


        // 오른 -> 왼
        before = next;
        next = arr[endX][startY];
        for(int i = startY; i<endY-1; i++){
            arr[endX][i] = arr[endX][i+1];
        }
        arr[endX][endY-1] = before;

        // 아래 -> 위
        for(int i = startX; i<endX-1; i++){
            arr[i][startY] = arr[i+1][startY];
        }
        arr[endX-1][startY] = next;

    }
    /*
    * 테두리에서 최소값 가져오기
    * */
    public int getMin(int startX, int startY, int endX, int endY){
        int min = Integer.MAX_VALUE;

        // 가로
        for(int i = startY; i<=endY; i++){
            min = Math.min(min, arr[startX][i]);
            min = Math.min(min, arr[endX][i]);
        }

        // 세로
        for(int i = startX+1; i<endX; i++){
            min = Math.min(min, arr[i][startY]);
            min = Math.min(min, arr[i][endY]);
        }

        return min;
    }
}
```

<br>

> ##### 참고 블로그
>
> https://settembre.tistory.com/380
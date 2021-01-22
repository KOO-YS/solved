# [Programmers] 하노이의 탑

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12946



> ### Solution

```java
import java.util.*;

class Solution {
    public static ArrayList<int[]> route;
    public int[][] solution(int n) {
        int[][] answer;

        route = new ArrayList<>();

        hanoiTop(n, 1, 2, 3);       // 기둥 3개

        answer = new int[route.size()][2];
        int index = 0;
        for(int[] arr : route){
            answer[index++] = arr;
        }
        return answer;
    }
    
    /**
     * n개의 고리를 
     * from 에서 to로 옮기는 방법
     */
    public void hanoiTop(int n, int from, int by, int to){
        if( n == 1 ){
            route.add(new int[]{from, to});
            return;
        }
        hanoiTop(n-1, from, to, by);    // 1개를 제외한 나머지를 두번째 기둥에 옮겨놓음
        hanoiTop(1, from, by, to);      // 제일 큰 원반을 마지막 세번째 기둥에 옮겨놓음
        hanoiTop(n-1, by, from, to);    // 두번째에 옮겨놓은 나머지 기둥들을 마지막 기둥에 옮김
    }
}
```



# [Programmers] N-Queen

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12952



> ### Solution

```java
class Solution {
    public static int count;
    /**
     *  한 열에 하나의 퀸이 들어가야 함
     */
    public int solution(int n) {

        int[] floor = new int[n+1];
        int level = 1;
        // 1번째 줄(level)의 i번째 칸에 둔다 -> floor
        for(int i=1; i<=n; i++){
            floor[level] = i;
            arrangeQueens(floor, level);
            floor[level] = 0;               // 다시 초기화
        }

        return count;
    }

    public void arrangeQueens(int[] floor, int level) {
        if(!checkCrossing(floor, level)) return;        // 서로 공격할 수 있다면
        if(level == floor.length-1){      // 완성됐다면
            count++;
            return;
        }
        for(int i=1; i<floor.length; i++){
            floor[level+1] = i;
            arrangeQueens(floor, level+1);
            floor[level+1] = 0;
        }
    }

    /**
     * floor[level] 에 퀸을 놓았을 때,
     * 가로, 세로, 대각선에서 겹치는 퀸이 있는지 여부 확인
     */
    public boolean checkCrossing(int[] floor, int level){
        for(int i=1; i<level; i++){
            // 세로
            if(floor[i] == floor[level]) return false;                          // 겹친다
            // 대각선
            if(Math.abs(floor[i]-floor[level]) == (level-i)) return false;      // 겹친다
        }
        return true;
    }
}
```


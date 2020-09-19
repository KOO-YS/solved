# [Programmers] 삼각 달팽이



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/68645



> ### Solution

```

class Solution {
    public int[] solution(int n) {
        int max = n*(n+1)/2;
        int[] answer =new int[max];

        int[][] snail = new int[n][n];

        for(int i=0; i<n; i++){
            for(int j=0; j<=i; j++){
                snail[i][j] = -1;
            }
        }

        int value = 1;
        int x = 0;
        int y = 0;
        snail[x][y] = value++;

        while(value<= max){
            while((value<=max) && !((x >= n-1) || (snail[x+1][y]!= -1))){      // left down
                snail[++x][y] = value++;
            }
            while((value<=max) && !((y >= n-1) || snail[x][y+1] != -1)){      // right straight
                snail[x][++y] = value++;
            }
            while((value<=max) && !((x<1) || (y<1) || (snail[x-1][y-1]!= -1)) ){      // left up
                snail[--x][--y] = value++;
            }
        }

        int idx = 0;
        for(int[] line : snail){
            for(int i : line){
                if(i > 0){
                    answer[idx++] = i;
                }
            }
        }
        return answer;
    }
}
```



**(미완성 -> 나중에 다시 해보기)**

```java
import java.util.*;

// 미완
class Solution {
    public int[] solution(int n) {
        List[] line  = new ArrayList[n];
        for(int i=0; i<n; i++){
            line[i] = new ArrayList<Integer>();
        }
        int max = n*(n+1)/2;
        int[] answer = new int[max];

        int value = 1;
        int gap = 0;
        int[] start = {0,0};
        int side = 0;       // 삼각형 선 긋는 방향
        for(int i=n; i>0; i--){         // 6 5 4 3 2 1
            if(side%3 == 0){                // left down
                for(int j=0; j<i; j++) {    // n 횟수 만큼 반복
                    line[start[0]+j].add(gap, value++);
                    if( j == i-1 ) start[0] = start[0]+j;
                }
            } else if(side%3 == 1) {        // straight right
                for(int j=0; j<i; j++){
                    if(line[start[0]].size()>1){
                        line[start[0]].add(line[start[0]].size()-gap, value++);
                    }
                    else {
                        line[start[0]].add(value++);
                    }
                    if( j == i-1 ) start[0] -= 1;
                }
            } else {                        // left up
                for(int j=0; j<i; j++){
//                    line[start[0]-j].add(value++);
                    if(line[start[0]-j].size()>2){
                        line[start[0]-j].add(line[start[0]].size()-gap, value++);
                    }
                    else {
                        line[start[0]-j].add(value++);
                    }
                    if( j == i-1 ) start[0] = start[0]-j+1;
                }
            }
            if(++side == 3) gap++;
        }
        int idx = 0;
        for (List l : line){
//            System.out.println(Arrays.toString(l.toArray()));
            for(int i=0; i<l.size(); i++){
                answer[idx++] = (int) l.get(i);
            }
        }
        return answer;
    }
}
```


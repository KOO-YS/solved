# [Programmers] 단속카메라



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42884
>



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[][] routes) {
        int answer = 1;

        Arrays.sort(routes, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[0] - o2[0];
            }
        });

       int end = routes[0][1];

       for(int[] r : routes){
            if(r[0] <= end){	// 겹치는 지점이 존재
                end = Math.min(end, r[1]);
            } else {
                answer++;		// 겹치지 않으므로 카메라 추가 
                end = r[1];
            }
       }

        return answer;
    }
}
```


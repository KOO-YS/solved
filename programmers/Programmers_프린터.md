# [Programmers] 프린터

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42587



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[] priorities, int location) {
        int answer = 1;
        // 우선순위 큐 정렬 (기준 : Descending )
        Queue<Integer> printer = new PriorityQueue<>(Collections.reverseOrder());

        for(int p : priorities){
            printer.offer(p);
        }

        while(!printer.isEmpty()){
            for(int i=0; i<priorities.length; i++){
                if(printer.peek() == priorities[i]){        // 가장 우선순위가 큰 값 발견
                    if(i == location){                      // 순환한 후 특정 위치의 값 발견
                        return answer;
                    }
                    printer.poll();
                    answer++;
                }
            }
        }
        return answer;
    }

}
```


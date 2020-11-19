# [Programmers] 더 맵게

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42626



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[] scoville, int K) {
        Queue<Integer> sorted = new PriorityQueue<>();
        for(int i : scoville){
            sorted.add(i);
        }

        int first, second;
        int count = 0;

        while(sorted.size() > 1){
            if(sorted.peek() >= K) return count;

            first = sorted.poll();
            second = sorted.poll();

            sorted.add(second*2 + first);

            count++;
        }

        if(sorted.peek() >= K ) return count;

        return -1;
    }
}
```

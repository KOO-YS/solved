# [Programmers] 귤 고르기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/138476
>


> ### Solution

```java
import java.util.Arrays;

class Solution {
    public int solution(int k, int[] tangerine) {
        int answer = 0;

        int[] countPerSize = new int[10000001];

        for (int size : tangerine) {
            countPerSize[size]++;
        }
        Arrays.sort(countPerSize);
        
        for (int i=countPerSize.length-1; i>=0; i--) {
            if (k <= 0) return answer;
            
            k -= countPerSize[i];
            answer++;
        }

        return answer;
    }
}
```


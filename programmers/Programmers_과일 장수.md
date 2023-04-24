# [Programmers] 과일 장수



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/135808
>


> ### Solution

```java
import java.util.Arrays;

class Solution {
    public int solution(int k, int m, int[] score) {
        int answer = 0;
        int start = score.length % m;
        
        Arrays.sort(score);
        
        for (int i = start; i<score.length; i+=m) {
            answer += score[i] * m;
        }
        return answer;
    }
}
```


# [Programmers] 위장



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42578



> ### Solution

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int solution(String[][] clothes) {
        int answer = 1;
        Map<String, Integer> kinds = new HashMap<>();
        for(int i=0; i<clothes.length; i++){
                kinds.put(clothes[i][1], kinds.getOrDefault(clothes[i][1], 0) + 1);
        }

        for(int num : kinds.values()){
            answer *= (num+1);
        }
        return answer-1;
    }
}
```


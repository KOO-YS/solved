# [Programmers] 폰켓몬

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/1845



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[] nums) {
        int pick = nums.length/2;

        Set<Integer> kinds = new HashSet<>();
        for(int i : nums){
            kinds.add(i);
        }
        if(kinds.size() > pick) return pick;
        else return kinds.size();
    }
}
```


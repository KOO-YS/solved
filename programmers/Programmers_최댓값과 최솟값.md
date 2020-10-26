# [Programmers] 최댓값과 최솟값

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12939



> ### Solution

```java
import java.util.StringTokenizer;

class Solution {
    public String solution(String s) {
        StringTokenizer token = new StringTokenizer(s, " ");
        int MIN = Integer.MAX_VALUE;
        int MAX = Integer.MIN_VALUE;

        while (token.hasMoreTokens()){
            int num = Integer.parseInt(token.nextToken());
            MIN = Math.min(MIN, num);
            MAX = Math.max(MAX, num);
        }

        return MIN+" "+MAX;
    }
}
```


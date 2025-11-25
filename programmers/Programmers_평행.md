# [Programmers] 평행

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/120875



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[][] dots) {
        Arrays.sort(dots, (a, b) -> Integer.compare(a[0], b[0]));
        return (dots[1][0] - dots[0][0]) * (dots[3][1] - dots[2][1]) == (dots[1][1] - dots[0][1]) * (dots[3][0] - dots[2][0])
                ? 1:0;
    }
}
```


# [Programmers] 없는 숫자 더하기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/86051

<br>

> ### solution

```java
import java.util.*;

class Solution {
    public int solution(int[] numbers) {
        int total = 45;
        for (int i : numbers) {
           total -= i;
        }

        return total;
    }
}
```

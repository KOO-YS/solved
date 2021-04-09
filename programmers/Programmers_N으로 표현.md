# [Programmers] N으로 표현



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42895
>



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int N, int number) {
        if(N == number) return 1;

        Set<Integer>[] counts = new Set[9];     // N을 i개 썼을 때 나오는 경우의 수
        int init = N;
        for(int i=1; i<counts.length; i++){
            counts[i] = new HashSet<>();
            counts[i].add(init);
            init += N*Math.pow(10, i);
        }

        for(int i=2; i<counts.length; i++){
            for(int j=1; j<i; j++){
                for (int n1 : counts[j]) {
                    for (int n2 : counts[i - j]) {
                        // 사칙연산
                        counts[i].add(n1 + n2);
                        counts[i].add(n1 - n2);
                        counts[i].add(n1 * n2);
                        if (n2 != 0) counts[i].add(n1 / n2);
                    }
                }
            if(counts[i].contains(number)) return i;
            }
        }

        return -1;
    }
}
```


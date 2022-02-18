# [Programmers] 숫자 게임

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12987



> ### Solution

```java
import java.util.Arrays;

class Solution {
        public int solution(int[] A, int[] B) {
        int answer = 0;

        Arrays.sort(A);
        Arrays.sort(B);

        int a = A.length -1;
        int b = B.length -1;

        while(a >= 0 && b >= 0) {
            if(A[a] < B[b]) {
                b--;
                answer++;
            }
            a--;
        }

        return answer;
    }

}
```


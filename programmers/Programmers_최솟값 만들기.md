# [Programmers] 최솟값 만들기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12941



> ### Solution

```java
import java.util.Arrays;
class Solution
{
    public int solution(int []A, int []B)
    {
        int answer = 0;

        Arrays.sort(A);
        Arrays.sort(B);
        int size = A.length;
        for(int i=0; i<size; i++){
            answer += A[i]*B[size-i-1];
        }

        return answer;
    }
}
```


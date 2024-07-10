# [Programmers] 기사단원의 무기 



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/136798

> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int number, int limit, int power) {
        int answer = 0;
        
        int[] divisor = new int[number + 1];
        
        for (int i=1; i<=number; i++) {
            int j = 1;
            while (Math.sqrt(i) >= j) {
                if ((i % j) == 0) {
                    divisor[i] ++;
                    if (Math.pow(j, 2) != i)
                        divisor[i] ++;
                }       
                j++;
            
                if (divisor[i] > limit) {
                    divisor[i] = power;
                    break;
                }
            }
            answer += divisor[i];   
        }   
        return answer;
    }
}
```


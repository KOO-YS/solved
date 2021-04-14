# [Programmers] 줄 서는 방법



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12936
>



> ### Solution

```java
import java.util.*;

class Solution {
    public long[] factorial;
    public int[] solution(int total, long k) {
        int[] answer = new int[total];
        int index = 0;

        int n = total;
        List<Integer> nums = new ArrayList<>();

        factorial = new long[n+1];
        factorial[0] = 1;
        for(int i=1; i<=total; i++){
            factorial[i] = factorial[i-1]*i;
            nums.add(i);
        }

        while(index != total){
            long part = factorial[n-1];

            if(k == 0) answer[index] = nums.remove(nums.size()-1);
            else if(k%part == 0) answer[index] = nums.remove((int) (k/part)-1);
            else answer[index] = nums.remove((int) (k/part));

            index++;
            n--;
            k = k%part;
        }

        return answer;
    }
}
```


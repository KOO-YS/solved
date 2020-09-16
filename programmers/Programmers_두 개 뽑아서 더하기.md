# [Programmers] 두 개 뽑아서 더하기 



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/68644



> ### Solution

```java
import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
        int[] answer;

        Set<Integer> sum = new HashSet<>();

        for(int i=0; i<numbers.length-1; i++){
            for(int j=i+1; j<numbers.length; j++){
                sum.add(numbers[i]+numbers[j]);
            }
        }

        Object[] convert =sum.toArray();

        answer = new int[convert.length];

        for(int i=0; i<convert.length; i++){
            answer[i] = Integer.parseInt(convert[i]+"");
        }

        Arrays.sort(answer);        // 확인차 정렬

        return answer;
    }
}
```


# [Programmers] 할인 행사



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/131701
>


> ### Solution

```java
import java.util.Set;
import java.util.HashSet;

class Solution {
    public int solution(int[] elements) {

        int[] arrSequence = new int[elements.length*2];
        System.arraycopy(elements, 0, arrSequence, 0, elements.length);
        System.arraycopy(elements, 0, arrSequence, elements.length, elements.length);

        Set<Integer> sumSet = new HashSet<>();

        for (int i=0; i< elements.length; i++) {
            int sum = arrSequence[i];
            sumSet.add(sum);
            for (int j=1; j< elements.length; j++) {
                sum += arrSequence[i+j];
                sumSet.add(sum);
            }
        }
        return sumSet.size();
    }
}
```


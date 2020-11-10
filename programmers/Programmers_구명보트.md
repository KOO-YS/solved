# [Programmers] 구명보트



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42885

> ### Solution

```java
import java.util.Arrays;

class Solution {
    public int solution(int[] people, int limit) {
        int answer = 0;
        Arrays.sort(people);
        int left = 0;
        int right = people.length -1;

        int boat = 0;
        while(left < right){
            boat = people[left] + people[right];        // 제일 무거운 사람과 제일 가벼운 사람 태움

            if(limit >= boat){      // 더 태울 수 있다
                left++;
                right--;            // next
            } else {                // 넘침 -> 무거운애밖에 못태움
                right--;
            }
            answer++;
        }
        if(left == right) answer++;

        return answer;
    }
}
```



*<u>한번에 최대 2명씩 태울 수 있다 -> 조건 간과</u>* 


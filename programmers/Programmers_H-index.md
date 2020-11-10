# [Programmers] H-index



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42747

> ### Solution

```java
import java.util.Arrays;

class Solution {
   public int solution(int[] citations) {
        int answer = 0;

        Arrays.sort(citations);
        int count = 0;

        int length = citations.length;
        for(int i=1; i<citations.length; i++){
            if(citations[i] < i) count++;
            if(i <= citations[length-i]){
                if(i >= count){
                    answer = Math.max(answer, i);
                }
            }
        }
        if(citations[length-1] < length) count++;
        if(length <= citations[0]){
            if(length >= count){
                answer = Math.max(answer, length);
            }
        }
        return answer;
    }
}
```

내가 풀었는데 내가 어떻게 푼거지...



1. h번 이상 인용된 논문이 h편 이상이다 -> h는 논문 갯수 내 범위를 가짐
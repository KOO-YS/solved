# [Programmers] 삼총사 



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/131705

> ### Solution

```java
class Solution {
    public int solution(int[] number) {
        int answer = 0;

        int first;
        int second;
        int third;
        for (int i=0; i<number.length-2; i++) {
            first = number[i];
            for (int j=i+1; j<number.length-1; j++) {
                second = number[j];
                for (int k=j+1; k<number.length; k++) {
                    third = number[k];

                    if ((first + second + third) == 0 ) answer++;
                }
            }
        }

        return answer;
    }
}
```


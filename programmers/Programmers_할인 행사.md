# [Programmers] 할인 행사



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/131127
>


> ### Solution

```java
class Solution {
    public int solution(String[] want, int[] number, String[] discount) {
        int answer = 0;

        for (int d=0; d<discount.length-9; d++) {
            int signUpDay = 0;
            for (int w=0; w<want.length; w++) {
                int wantedCount = 0;
                for (int i=d; i<d+10; i++) {
                    if (want[w].equals(discount[i]))
                        wantedCount++;
                }
                if (wantedCount < number[w]) break;     // 원하는 수량만큼 연속적이지 못하다
                else signUpDay++;
                
            }
            if (signUpDay == want.length)
                answer++;
        }


        return answer;
    }
}
```


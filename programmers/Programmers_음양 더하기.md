# [Programmers] 음양 더하기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/76501
>



> ### Solution

```java
class Solution {
    public int solution(int[] absolutes, boolean[] signs) {
        int answer = 0;

        for(int i=0; i<absolutes.length; i++){
            int flag = 1;
            if(signs[i]) flag = 1;
            else flag = -1;
            answer += (absolutes[i]*flag);
        }

        return answer;
    }
}
```


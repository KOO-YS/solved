# [Programmers] 약수의 개수와 덧셈



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/77884

<br>

> ### solution

```java
class Solution {
    public int solution(int left, int right) {
        int answer = 0;
        // 약수가 홀수개인 수 -> 한 정수의 제곱
        for (int i=left; i<= right; i++) {
            // 0으로 나누어 떨어지지 않는 한 i의 제곱수이 아니다
            if (Math.sqrt(i) != 0) answer += i;
            //if ((Math.sqrt(i) % 1) > 0) answer += i;
            else answer -= i;
        }

        return answer;
    }
}
```

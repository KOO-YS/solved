# [Programmers] 피자 나눠 먹기 (1)



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/120814

> ### Solution

```java
class Solution {
    public int solution(int n) {
        int answer = (n%7 == 0)? n/7 : n/7+1;
        return answer;
    }
}
```


# [Programmers] 나머지가 1이 되는 수 찾기

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/87389

<br>

> ### solution

```java
class Solution {
    public int solution(int n) {
        int answer = 1;

        while (n > answer) {
            if (n%answer == 1) return answer;
            answer ++;
        }
        return answer;
    }
}
```

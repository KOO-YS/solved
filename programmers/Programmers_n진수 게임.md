# [Programmers] n진수 게임

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/17687

<br>

> ### solution

```java
class Solution {
    
    public String solution(int n, int t, int m, int p) {
        String answer = "";
        int total = t * m;

        int num = 0;
        String game = "";

        while (game.length() < total) {
            game += Integer.toString(num, n);
            num++;
        }

        int order = 0;
        for (int i = 0; i<t; i++) {
            answer += game.charAt(order + (p - 1));
            order += m;
        }

        return answer.toUpperCase();
    }
}
```

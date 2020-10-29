# [Programmers] 점프와 순간 이동



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12980

> ### Solution

```java
public class Solution {
    public int solution(int n) {
        int ans = 0;
        while (n > 0){
            if(n%2 == 1) ans++;
            n /= 2;
        }
        return ans;
    }
}
```


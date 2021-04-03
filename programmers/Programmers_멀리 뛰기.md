# [Programmers] 멀리 뛰기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12914
>



> ### Solution
>

```java
class Solution {
    public long solution(int n) {
        
        if(n <= 2) return n;
        
        // dp(n) = dp(n-1) + dp(n-2)
        long[] dp = new long[n+1];

        dp[1] = 1;
        dp[2] = 2;
        for(int i=3; i<=n; i++){
            dp[i] = (dp[i-1] +dp[i-2])%1234567;
        }

        return dp[n];
    }
}
```


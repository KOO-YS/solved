# [Programmers] 2 x n 타일링 



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12900

> ### Solution

```java
class Solution {
   public int solution(int n) {
        memo = new int[n+1];
        int answer = tiling(n);
        return answer;
    }
    public int[] memo;
    public int tiling(int width){
        if(width == 1) return memo[1] = 1;
        else if(width == 2) return memo[2] = 2;
        else if(memo[width] != 0) return memo[width];

        memo[width] = (tiling(width-1) + tiling(width-2)) % 1000000007;

        return memo[width];
    }

}
```


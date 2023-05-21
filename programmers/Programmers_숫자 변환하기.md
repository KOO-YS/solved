# [Programmers] 숫자 변환하기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/154538



> ### Solution

```java
class Solution {
    public int solution(int x, int y, int n) {
		int answer = 0;
		int[] dp = new int[y+1];

		for (int i=x+1; i<dp.length; i++) {
			int way01 = (i - n) >= x ? dp[i-n] : Integer.MAX_VALUE;
			int way02 = (i/2 >= x) && (i%2 == 0) ? dp[i/2] : Integer.MAX_VALUE;
			int way03 = (i/3 >= x) && (i%3 == 0) ? dp[i/3] : Integer.MAX_VALUE;

			int least = Math.min(Math.min(way01, way02), way03);

			dp[i] = (least < Integer.MAX_VALUE) ? least + 1 : Integer.MAX_VALUE;
		}

		return dp[y] < Integer.MAX_VALUE ? dp[y] : -1;
	}
}
```


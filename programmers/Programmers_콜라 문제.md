# [Programmers] 콜라 문제



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/132267

> ### Solution

```java
class Solution {
    public int solution(int a, int b, int n) {
		int answer = 0;
		int bottle = n;
		
		while (a <= bottle) {
			answer += (bottle / a) * b;
			bottle = (bottle / a) * b + (bottle % a);
		}
		
		return answer;
	}
}
```


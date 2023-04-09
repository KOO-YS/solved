# [Programmers] 크기가 작은 부분 



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/147355

> ### Solution

```java
class Solution {
    public int solution(String t, String p) {
		int answer = 0;
		int characterLength = p.length();
		long numberP = Long.parseLong(p);
		long numberT;

		for (int i=0; i< t.length() - characterLength+1; i++) {
			numberT = Long.parseLong(t.substring(i, i+characterLength));
			if (numberT <= numberP) answer++;
		}

		return answer;
	}
}
```


# [Programmers] 푸드 파이트 대회



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/134240

> ### Solution

```java
class Solution {
    public String solution(int[] food) {
		StringBuilder answer = new StringBuilder("0");
		int count;
		String repeatNumber;
		for (int i = food.length-1; i>0; i--) {
			count = food[i]/2;
			repeatNumber = String.valueOf(i).repeat(count);
			answer.insert(0, repeatNumber);
			answer.append(repeatNumber);
		}
		return answer.toString();
	}
}
```


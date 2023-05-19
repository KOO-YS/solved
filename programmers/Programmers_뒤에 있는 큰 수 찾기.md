# [Programmers] 뒤에 있는 큰 수 찾기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/154539
>



> ### Solution

```java
import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
		int[] answer = new int[numbers.length];

		Stack<int[]> stack = new Stack<>();
		stack.push(new int[] {0, numbers[0]});

		for (int i=1; i<numbers.length; i++) {
			while (!stack.isEmpty() && stack.peek()[1] < numbers[i]) {
				int[] element = stack.pop();
				answer[element[0]] = numbers[i];
			}
			stack.push(new int[]{i, numbers[i]});
		}

		while (!stack.isEmpty()) {
			answer[stack.pop()[0]] = -1;
		}

		return answer;
	}
}
```


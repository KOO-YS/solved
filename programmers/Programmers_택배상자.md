# [Programmers] 택배상자



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/131704#qna



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[] order) {
		int answer = 0;

		int index = 0;
		int turn = 1;
		Stack<Integer> stack = new Stack<>();

		while (true) {
			if (!stack.empty() && order[index] == stack.peek()) {
				answer++;
				index++;
				stack.pop();

				continue;
			}

			if (turn > order.length)
				break;

			if (order[index] == turn) {
				answer++;
				index++;
				turn++;
				continue;
			}
			stack.push(turn);
			turn++;
		}
		
		return answer;
	}
}
```

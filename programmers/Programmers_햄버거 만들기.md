# [Programmers] 햄버거 만들기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/133502

# 구연수 #자챌완

> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(int[] ingredient) {
		int answer = 0;
        String burger = "1231";
        int[] recipe = new int[]{1,2,3,1};

        Stack<Integer> stack = new Stack<>();

        for (int i : ingredient) {
            stack.push(i);

            if (stack.size() >= 4) {
                boolean order = (stack.get(stack.size() - 1) == 1) && (stack.get(stack.size() - 2) == 3) && (stack.get(stack.size() - 3) == 2) && (stack.get(stack.size() - 4) == 1);
                if (order) {
                    for (int j=0; j<4; j++) stack.pop();
                    answer ++;
                }
            }
        }

        return answer;
	}
}
```

---

> ### wrong
> 실패 (시간 초과)

```java
import java.util.*;

class Solution {
    public int solution(int[] ingredient) {
		int answer = 0;
		String burger = "1231";

		String ingredientStr = Arrays.toString(ingredient).replaceAll("[^0-9]","");

		while (ingredientStr.contains(burger)) {
			ingredientStr = ingredientStr.replaceFirst(burger, "");
			answer++;
		}

		return answer;
	}

}
```


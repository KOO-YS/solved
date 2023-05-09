# [Programmers] 햄버거 만들기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/133502



> ### Solution

```java
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


# [Programmers] 롤케이크 자르기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/132265
>



> ### Solution

```java
import java.util.*;

class Solution {
    
    public static int solution(int[] topping) {
		int answer = 0;
		Set<Integer> count = new HashSet<>();
		Map<Integer, Integer> map = new HashMap<>();

		for (int i = 0; i < topping.length; i++) {
			map.put(topping[i], map.getOrDefault(topping[i], 0) + 1);
		}

		for (int i = 0; i < topping.length; i++) {
			count.add(topping[i]);
			map.put(topping[i], map.get(topping[i]) - 1);
			
			if (map.get(topping[i]) == 0) {
				map.remove(topping[i]);
			}
			if (count.size() == map.size()) {
				answer++;
			}
		}

		return answer;
	}
}
```


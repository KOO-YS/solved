# [Programmers] 대충 만든 자판

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/160586

```
import java.util.*;

class Solution {
    public int[] solution(String[] keymap, String[] targets) {
		int[] answer = new int[targets.length];
		Map<Character, Integer> map = new HashMap<>();

		for (String key : keymap) {
			for (int j = 0; j < key.length(); j++) {
				char k = key.charAt(j);
				if (map.containsKey(k)) {
					map.put(k, Math.min(map.get(k), j + 1));
				} else
					map.put(k, j + 1);
			}
		}
		for (int i=0; i<targets.length; i++) {
			answer[i] = pressLeastKey(map, targets[i]);
		}
		return answer;
	}

	public int pressLeastKey(Map<Character, Integer> map, String target) {
		int count = 0;

		for (char t : target.toCharArray()) {
			if (!map.containsKey(t))
				return -1;
			else
				count += map.get(t);
		}
		return count;
	}
}
```


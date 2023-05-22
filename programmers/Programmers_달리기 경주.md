# [Programmers] 달리기 경주

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/178871



> ### Solution

```java
import java.util.*;

class Solution {
    public String[] solution(String[] players, String[] callings) {
		String[] answer = {};
		Map<String, Integer> indexMap = new HashMap<>();

		for (int i=0; i<players.length; i++) {
			indexMap.put(players[i], i);
		}

		for (String pass : callings) {
			int temp = indexMap.get(pass);
			String behind = players[temp - 1];

			indexMap.put(behind, temp);
			indexMap.put(pass, temp-1);

			players[temp] = behind;
			players[temp-1] = pass;
		}

		return players;
	}
}
```

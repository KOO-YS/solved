# [Programmers] 혼자 놀기의 달인



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/131130



> ### Solution

```java
import java.util.*;

class Solution {
    int[] parents;
	boolean[] visited;

	public int solution(int[] cards) {
		
		Map<Integer, Integer> countByParent = new HashMap<>();
		parents =  new int[cards.length];
		visited = new boolean[cards.length];

		for(int i=0; i<cards.length; i++){
			parents[i] = cards[i];
			parents[i]--;
		}

		int num;
		for(int i=0; i<cards.length; i++){
			if(!visited[i]){
				num = find(i, visited);
			}else{
				num = parents[i];
			}
			countByParent.put(num, countByParent.getOrDefault(num, 0) + 1);
		}

		if(countByParent.size() < 2)
			return 0;

		List<Integer> countSort = new ArrayList<>(countByParent.values());
		countSort.sort((o1, o2) -> o2-o1);
		return countSort.get(0) * countSort.get(1);
	}


	int find(int a, boolean[] visited){
		if(a == parents[a] || visited[a]){
			return a;
		}
		visited[a] = true;
		return parents[a] = find(parents[a], visited);
	}
}
```


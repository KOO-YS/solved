# [Programmers] 혼자 놀기의 달인



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/131130



> ### Solution

```java
int[] parents;
	public int solution(int[] cards) {
		int answer = 0;
		parents = new int[cards.length];

		for (int i = 0; i<cards.length; i++) {
			parents[i] = i;
			cards[i] --;
		}
		Map<Integer, Integer> countByParent = new HashMap<>();

		for (int i=0; i<cards.length; i++) {
			union(i, cards[i]);
		}

		System.out.println(Arrays.toString(parents));

		return answer;
	}



	public int find(int x) {
		if (parents[x] == x)
			return x;
		else return parents[x] = find(parents[x]);
	}

	public int union(int x, int y) {
		x = find(x);
		y = find(y);

		if (x == 6) {
			System.out.println();
		}
		if (x > y)
			return parents[x] = y;
		else
			return parents[y] = x;
	}
```


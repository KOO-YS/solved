# [Programmers] 교점에 별 만들기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/87377

> ### Solution

```java
import java.util.*;

class Solution {
    public String[] solution(int[][] line) {
		String[] answer;

		int minX = Integer.MAX_VALUE;
		int minY = Integer.MAX_VALUE;
		int maxX = Integer.MIN_VALUE;
		int maxY = Integer.MIN_VALUE;

		List<int[]> intersection = new ArrayList<>();

		for (int i=0; i<line.length-1; i++) {
			for (int j=i+1; j<line.length; j++) {
				int[] one = line[i];
				int[] two = line[j];

				long denominator = (long) one[0]*two[1] - (long) one[1]*two[0];
				if (denominator == 0)
					continue;

				long numeratorX = (long) one[1]*two[2] - (long) one[2]*two[1];
				long numeratorY = (long) one[2]*two[0] - (long) one[0]*two[2];

				if (numeratorX%denominator != 0 || numeratorY%denominator != 0)
					continue;

				int x = (int) (numeratorX/denominator);
				int y = (int) (numeratorY/denominator);

				intersection.add(new int[]{x, y});
				minX = Math.min(minX, x);
				minY = Math.min(minY, y);
				maxX = Math.max(maxX, x);
				maxY = Math.max(maxY, y);
			}
		}

		char [][] print = new char[maxY - minY + 1][maxX - minX + 1];
		for (char[] chars : print) {
			Arrays.fill(chars, '.');
		}

		for (int[] each : intersection) {
			int x = each[0]- minX;
			int y = maxY - each[1];

			print[y][x] = '*';
		}

		answer = new String[maxY - minY + 1];

		for (int i=0; i<answer.length; i++) {
			answer[i] = new String(print[i]);
		}

		return answer;
	}
}
```

---

<br>

> ### Wrong

```java
import java.util.*;

public String[] solution(int[][] line) {
		String[] answer;

		int minX = Integer.MAX_VALUE;
		int minY = Integer.MAX_VALUE;
		int maxX = Integer.MIN_VALUE;
		int maxY = Integer.MIN_VALUE;

		List<int[]> intersection = new ArrayList<>();

		for (int i=0; i<line.length-1; i++) {
			for (int j=i+1; j<line.length; j++) {
				int[] one = line[i];
				int[] two = line[j];

				int denominator = one[0]*two[1] - one[1]*two[1];
				if (denominator == 0)
					continue;

				int numeratorX = one[1]*two[2] - one[2]*two[1];
				int numeratorY = one[1]*two[2] - one[2]*two[1];

				if (numeratorX%denominator != 0 || numeratorY%denominator != 0)
					continue;

				int x = numeratorX/denominator;
				int y = numeratorY/denominator;

				intersection.add(new int[]{x, y});
				minX = Math.min(minX, x);
				minY = Math.min(minY, y);
				maxX = Math.max(maxX, x);
				maxY = Math.max(maxY, y);
			}
		}

		char [][] print = new char[maxY - minY + 1][maxX - minX + 1];
		for (char[] chars : print) {
			Arrays.fill(chars, '.');
		}

		for (int[] each : intersection) {
			int x = each[0]- minX;
			int y = maxY - each[1];

			print[y][x] = '*';
		}

		answer = new String[maxY - minY + 1];

		for (int i=0; i<answer.length; i++) {
			answer[i] = new String(print[i]);
			System.out.println(new String(print[i]));
		}

		return answer;
	}
```


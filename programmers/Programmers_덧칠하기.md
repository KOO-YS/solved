# [Programmers] 덧칠하기

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/161989?language=java



> ### Solution

```java
class Solution {
    /**
	 *
	 * @param wall 벽의 전체 길이(n)
	 * @param roll 롤러로 한 번에 칠할 수 있는 벽 길이(m)
	 * @param section 페인트를 다시 칠해야 하는 구역의 번호 (오름차순)
	 * @return 롤러로 페인트칠해야 하는 최소 횟수
	 */
	public int solution(int wall, int roll, int[] section) {
		int answer = 0;
		int index = 0;
		int startIndex = section[0];

		while (index < section.length) {
			int current = section[index];
			startIndex = index;

			for (int i=startIndex; i< section.length; i++) {
				if (section[i] < current+roll)
					index = i + 1;
				else break;
			}
			answer ++;
		}

		return answer;
	}

}
```


# [Programmers] 게임 맵 최단거리

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/1844



> ### Solution

```java
import java.util.*;

class Solution {
    int[] dx = {0, 1, 0, -1};
	int[] dy = {-1, 0, 1, 0};

	public int solution(int[][] maps) {
		int n = maps.length;
		int m = maps[0].length;
		int[][] visited = new int[n][m];

		Queue<int[]> queue = new LinkedList<>();
		queue.add(new int[]{0, 0});
		visited[0][0] = 1;

		while (!queue.isEmpty()) {
			int[] now = queue.poll();
			for (int i=0; i<4; i++) {
				int nextX = now[0] + dx[i];
				int nextY = now[1] + dy[i];

			 	if (nextX < 0 || nextX >= n) continue;
			 	if (nextY < 0 || nextY >= m) continue;

				 if (visited[nextX][nextY] == 0 && maps[nextX][nextY] == 1) {
					 visited[nextX][nextY] = visited[now[0]][now[1]] + 1;
					 queue.add(new int[]{nextX, nextY});
				 }
			}

		}
		return (visited[n-1][m-1] == 0)? -1 : visited[n-1][m-1];
	}
}
```

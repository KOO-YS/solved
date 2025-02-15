# [Programmers] [PCCE 기출문제] 9번 / 이웃한 칸



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/250125

> ### Solution

```java
import java.util.*;

class Solution {
    
    int[] dh = {-1, 0, 1, 0};
    int[] dw = {0, 1, 0, -1};

    public boolean isBoundary(String[][] board, int h, int w) {
        return h >= 0 && h < board.length && w >= 0 && w < board[0].length;
    }

    public int solution(String[][] board, int h, int w) {
        int answer = 0;

        String searchColor;
        boolean[][] visited = new boolean[board.length][board[0].length];

        // 탐색 기준 결정
        searchColor = board[h][w];
        visited[h][w] = true;

        for (int k = 0; k < 4; k++) {
            int nextH = h + dh[k];
            int nextW = w + dw[k];

            if (isBoundary(board, nextH, nextW)
                    && !visited[nextH][nextW]
                    && board[nextH][nextW].equals(searchColor)) {
                answer++;
            }
        }

        return answer;
    }
}
```

### 주의사항
- board[h][w] 주변 '위,아래,오른쪽,왼쪽' 이웃한 칸만 체크할 것 
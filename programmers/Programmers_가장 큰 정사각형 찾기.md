# [Programmers] 가장 큰 정사각형 찾기

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12905

<br>

> ### solution

```java
class Solution
{
    public int solution(int [][]board) {
        int answer = board[0][0];
        
        int row = board.length;
        int column = board[0].length;

        // if (i > 0) ->  (왼쪽대각선상단, 상단, 왼쪽) 중 최솟값 + 1
        int min;
        for (int i=1; i<row; i++) {
            for (int j=1; j<column; j++) {
                if (board[i][j] == 0) continue;
                min = Math.min(board[i-1][j-1], Math.min(board[i-1][j], board[i][j-1]));
                board[i][j] = min + 1;
                answer = Math.max(answer, board[i][j]);
            }
        }
        return (int)Math.pow(answer, 2);
    }
}
```

<br>



#### 고려한 테스트 케이스 예시

```java
@Test
    public void test() {
        Solution s = new Solution();

        Assert.assertThat(s.solution(new int[][]{{0, 1, 1, 1}, {1, 1, 1, 1}, {1, 1, 1, 1}, {0, 0, 1, 0}}), is(9));
        Assert.assertThat(s.solution(new int[][]{{0,0,1,1},{1,1,1,1}}), is(4));
        Assert.assertThat(s.solution(new int[][]{{0, 0},{0, 0}}), is(0));	// -> 1이 없을 수도 있다
        Assert.assertThat(s.solution(new int[][]{{1},{0}}), is(1));
        Assert.assertThat(s.solution(new int[][]{{1, 0},{0, 0}}), is(1));	// -> for문이 index [1][1] 부터 돌다보니 {0,0}에 있는 1을 체크하지 못하는 경우가 생겼다
        
    }
```






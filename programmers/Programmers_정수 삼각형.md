# [Programmers] 정수 삼각형



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/43105
>



> ### Solution

```java
class Solution {
    public int solution(int[][] triangle) {
        for(int i=triangle.length-1; i>0; i--){		// 아래칸부터 윗칸으로 조회
            for(int j=0; j<triangle[i].length-1; j++){
                // 아래 칸의 j, j+1 번째 숫자 중 더 큰 숫자를 바로 윗 칸의 j번째 칸에 합쳐놓는다
                triangle[i-1][j] += Math.max(triangle[i][j], triangle[i][j+1]);
            }
        }
        return triangle[0][0];		// 꼭대기에 합쳐진 가장 큰 합
    }
}
```


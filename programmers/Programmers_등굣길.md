# [Programmers] 등굣길



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42898

<br>

> ### solution

```java
class Solution {
    public int solution(int m, int n, int[][] puddles) {
        int[][] way = new int[n][m];

        int answer = 0;
        for(int[] p : puddles){
            way[p[1]-1][p[0]-1] = -1;       // 물 웅덩이 표시
        }

        way[0][0] = 1;

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++) {
                if(way[i][j] == -1){
                    way[i][j] = 0;
                    continue;
                }

                if(i != 0) way[i][j] += way[i - 1][j] % 1000000007;
                if(j != 0) way[i][j] += way[i][j - 1] % 1000000007;
            }
        }

        return way[n-1][m-1] % 1000000007;
    }
}
```
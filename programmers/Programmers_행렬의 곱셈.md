# [Programmers] 행렬의 곱셈

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12949



> ### Solution

```java
class Solution {
    public int[][] solution(int[][] arr1, int[][] arr2) {
        // 첫번째 행렬의 행 개수 * 두번째 행렬의 열 개수
        int[][] answer = new int[arr1.length][arr2[0].length];

        int len;
        for(int i=0; i<arr1.length; i++){
            for(int j=0; j<arr2[0].length; j++){
                len = 0;
                while(len < arr2.length){
                    answer[i][j] += (arr1[i][len] * arr2[len][j]);
                    len++;
                }
            }
        }
        return answer;
    }
}
```


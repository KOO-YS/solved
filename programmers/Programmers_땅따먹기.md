# [Programmers] 땅따먹기

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12913



> ### Solution
> dp 활용

```java
class Solution {
    int solution(int[][] land) {

        for (int i=1; i<land.length; i++) {
            land[i][0] += Math.max(Math.max(land[i-1][1], land[i-1][2]), land[i-1][3]);
            land[i][1] += Math.max(Math.max(land[i-1][0], land[i-1][2]), land[i-1][3]);
            land[i][2] += Math.max(Math.max(land[i-1][1], land[i-1][0]), land[i-1][3]);
            land[i][3] += Math.max(Math.max(land[i-1][1], land[i-1][2]), land[i-1][0]);
        }
        return Math.max(
            Math.max(land[land.length-1][0], land[land.length-1][1]),
            Math.max(land[land.length-1][2], land[land.length-1][3])
        );
    }
}
```







##### 시간초과

```java
class Solution {
    public static int max;
    public int solution(int[][] land) {
        max = 0;

        for(int i=0; i<land[0].length; i++){
            step(i, 1, land, land[0][i]);
        }

        return max;
    }
    public void step(int block, int row, int[][] land, int grade){
        if(land.length == row){
            max = Math.max(max, grade);
            return;
        }
        for(int i=0; i<land[row].length; i++){
            if(i != block) {
                step(i, row + 1, land, grade + land[row][i]);
            }
        }
    }
}
```


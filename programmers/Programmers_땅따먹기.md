# [Programmers] 땅따먹기

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12913



> ### Solution

```java

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


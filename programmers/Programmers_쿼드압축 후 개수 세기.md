# [Programmers] 쿼드압축 후 개수 세기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/68636



> ### Solution

```java
class Solution {
    public static int[] answer;
    public int[] solution(int[][] arr) {
        answer = new int[2];

        quadTree(arr, 0, 0, arr.length);

        return answer;
    }
    public static void quadTree(int[][] arr, int col, int row, int len){
        if(check(arr, col, row, len)){
            answer[arr[col][row]]++;
        } else{
            quadTree(arr, col, row, len/2);
            quadTree(arr, col, row+(len/2), len/2);
            quadTree(arr, col+(len/2), row, len/2);
            quadTree(arr, col+(len/2), row+(len/2), len/2);
        }
    }

    public static boolean check(int[][] arr, int col, int row, int len){
        int value = arr[col][row];
        for(int i=col; i<col+len; i++){
            for(int j=row; j<row+len; j++){
               if(arr[i][j] != value) return false;
            }
        }
        return true;
    }
}
```


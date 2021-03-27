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

> ### Another

```java
class Solution {
    public int zero;
    public int one;
    public int[] solution(int[][] arr) {
        int[] answer = {};
        zero = 0;
        one = 0;
        zip(arr, 0, 0, arr.length);
        return new int[]{zero, one};
    }

    public void zip(int[][] arr, int startX, int startY, int term){
        if(term == 1){
            if(arr[startX][startY] == 0) zero++;
            else one++;
            return;
        }
        int mark = arr[startX][startY];     // 영역 값을 비교할 기준점
        
        for(int i=0; i<term; i++){
            for(int j=0; j<term; j++){
                if(arr[startX+i][startY+j] != mark){        // 압축할 수 없다
                    int nextTerm = term/2;
                    // 분할 검색
                    zip(arr, startX, startY, nextTerm);
                    zip(arr, startX, startY+nextTerm, nextTerm);
                    zip(arr, startX+nextTerm, startY, nextTerm);
                    zip(arr, startX+nextTerm, startY+nextTerm, nextTerm);
                    return;
                }
            }
        }
        if(mark == 0) zero++;
        else one++;
    }
}
```


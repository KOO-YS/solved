# [Programmers] 쿼드압축 후 개수 세기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/68636



> ### Solution

```java
class Solution {
    public static int result[];
    public static int[] solution(int[][] arr) {
        result = new int[2];
        quadTree(arr, 0, 0, arr.length);

        return result;
    }

    public static void quadTree(int[][] arr, int row, int col, int N) {
        if(fillWith(arr, row, col, N)) {
            result[arr[row][col]]++;        // 0 or 1의 개수 추가
        }else {
            int size = N/2;

            //해당 영역을 다시 4분할 하여 탐색
            quadTree(arr, row, col, size);
            quadTree(arr, row, col + size, size);
            quadTree(arr, row + size, col, size);
            quadTree(arr, row + size, col + size, size);
        }
    }

    //해당 영역이 전부 1이거나 0인 경우 해당 배열 원소값 +1
    public static boolean fillWith(int[][] arr, int row, int col, int size) {
        int t = arr[row][col];

        for(int i=row; i < row+size; i++) {
            for(int j=col; j < col+size; j++) {
                if(t != arr[i][j]) return false;
            }
        }
        return true;
    }
}
```


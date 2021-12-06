# [Programmers] 최소 직사각형

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/86491

<br>

> ### solution

```java
class Solution {
    public int solution(int[][] sizes) {
        int width = 0, height = 0;
        for (int[] arr : sizes) {
            width = Math.max(width, Math.max(arr[0], arr[1]));
            height = Math.max(height, Math.min(arr[0], arr[1]));
        }
        return width * height;
    }
}
```

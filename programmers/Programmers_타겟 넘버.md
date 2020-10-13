# [Programmers] 타겟 넘버

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/43165



> ### Solution

```java
class Solution {
    public int solution(int[] numbers, int target) {
        count = 0;
        bfs(numbers, 0, 0, target);
        return count;
    }
    public static int count;
    public void bfs(int[] number, int index, int sum, int target){
        int sum1 =sum + number[index];
        int sum2 = sum - number[index++];
        if(index == number.length){
            if(sum1 == target) {
                count++;
            }
            if(sum2 == target) {
                count++;
            }
        } else {
            bfs(number, index, sum1, target);
            bfs(number, index, sum2, target);
        }
    }
}
```

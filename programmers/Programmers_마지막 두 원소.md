# [Programmers] 마지막 두 원소



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/181927

<br>

> ### solution

```java
class Solution {
    public int[] solution(int[] num_list) {
        int size = num_list.length;
        int[] answer = new int[size + 1];
        
        for (int i=0; i<size; i++) {
            answer[i] = num_list[i];
        }
        
        if (num_list[size - 2] < num_list[size -1])
            answer[size] = num_list[size - 1] - num_list[size - 2];
        else
            answer[size] = num_list[size - 1] * 2;
        
        return answer;
    }
}

```

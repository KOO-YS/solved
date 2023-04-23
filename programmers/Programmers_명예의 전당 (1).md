# [Programmers] 명예의 전당 (1)



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/138477
>


> ### Solution

```java
import java.util.PriorityQueue;
import java.util.Queue;

class Solution {
    public int[] solution(int k, int[] score) {
        int[] answer = new int[score.length];

        Queue<Integer> rank = new PriorityQueue<>();

        for (int i = 0; i<score.length; i++) {
            if (rank.size() < k)
                rank.add(score[i]);
            else {
                rank.add(Math.max(rank.poll(), score[i]));
            }
            answer[i] = rank.peek();
        }

        return answer;
    }
}
```


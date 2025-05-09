# [Programmers] 과제 진행하기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/176962



> ### Solution

```java
```

---

> ### Wrong
- `멈춰둔 과제가 여러 개일 경우, 가장 최근에 멈춘 과제부터 시작합니다` 조건 충족 X
```java
import java.util.*;

class Solution {
    public String[] solution(String[][] plans) {
        String[] answer = new String[plans.length];
        int answerIndex = 0;
        Stack<Task> keep = new Stack<>();

        Deque<Task> queue = new LinkedList<>();
        Arrays.stream(plans)
                .map(plan -> new Task(plan[0], plan[1], plan[2]))
                .sorted()
                .forEach(queue::addLast);

        while (queue.size() > 1) {
            Task now = queue.pop();
            Task next = queue.peekFirst();

            if (now.startTime + now.taken <= next.startTime) {
                answer[answerIndex] = now.name;
                answerIndex++;
            } else {
                now.taken = (now.startTime + now.taken) - next.startTime;
                queue.add(now);
            }
        }
        if (!queue.isEmpty())
            answer[answerIndex] = queue.pop().name;

        return answer;
    }

}

class Task implements Comparable<Task> {
    String name;
    int startTime;
    int taken;

    public Task(String name, String startTime, String taken) {
        this.name = name;
        this.startTime = convertTime(startTime);
        this.taken = Integer.parseInt(taken);
    }

    public int convertTime(String timeStr) {
        String[] split = timeStr.split(":");
        return Integer.parseInt(split[0]) * 60 + Integer.parseInt(split[1]);
    }

    @Override
    public int compareTo(Task o) {
        return this.startTime - o.startTime;
    }
}
```


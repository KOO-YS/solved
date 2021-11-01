# [Programmers] 이중우선순위큐



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42628

<br>

> ### solution

```java
import java.util.*;

class Solution {
    public int[] solution(String[] operations) {
        int[] answer = {0, 0};

        PriorityQueue<Integer> minQueue = new PriorityQueue<>();
        PriorityQueue<Integer> maxQueue = new PriorityQueue<>(Comparator.reverseOrder());

        StringTokenizer tokenizer;
        for(String s : operations){
            tokenizer = new StringTokenizer(s, " ");

            String oper = tokenizer.nextToken();
            int num = Integer.parseInt(tokenizer.nextToken());
            if(oper.equals("I")){
                minQueue.add(num);
                maxQueue.add(num);
            } else {
                    if (num < 0) {        // D -1 (최솟값 삭제)
                     	// max에서도 최솟값을 같이 삭제해줌
                        maxQueue.remove(minQueue.peek());
                        // 최솟값 삭제
                        minQueue.poll();
                    } else {                // D 1 (최댓값 삭제)
                        // min에서도 최댓값을 같이 삭제해줌
                        minQueue.remove(maxQueue.peek());
                        // 최댓값 삭제
                        maxQueue.poll();
                    }
            }
        }

        if(minQueue.isEmpty() || maxQueue.isEmpty()) return answer;
        return new int[]{maxQueue.poll(), minQueue.poll()};
    }
}
```



> ### 오답

```java
import java.util.*;

class Solution {
    public int[] solution(String[] operations) {
        int[] answer = {0, 0};

        int front = 0;
        int back = 0;

        List<Integer> list = new ArrayList<>();

        StringTokenizer tokenizer;
        for(String s : operations){
            tokenizer = new StringTokenizer(s, " ");

            String oper = tokenizer.nextToken();
            int num = Integer.parseInt(tokenizer.nextToken());
            if(oper.equals("I")){
                list.add(num);
            } else {
                if(num < 0) front++;        // D -1 (최솟값 삭제)
                else back++;                // D 1 (최댓값 삭제)
            }
        }
        Collections.sort(list);

        if(list.size() - (front + back) <= 0) return answer;

        return new int[]{list.get(list.size() - 1 - back), list.get(front)};

    }
}
```

> 삭제할 최소 최대값의 개수를 가지고 마지막에 제외하였지만, 
>
> 문제는 **'명령어가 들어왔을 당시에 바로 명령어를 수행해야 한다'**

# [Programmers] 디스크 컨트롤러



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/42627

<br>

> ### solution

```java
import java.util.*;

class Solution {
    public int solution(int[][] jobs) {
        int answer = 0;

        int time = 0;     // 작업 시작 시간
        int index = 0;
        
        int count = 0;
        Queue<Disk> queue = new PriorityQueue<>();

        Arrays.sort(jobs, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[0] - o2[0];
            }
        });

        while(count != jobs.length){
            // 시작 가능한 작업들 우선 순위 큐에 담기
            while(index != jobs.length && time >= jobs[index][0]){
                queue.add(new Disk(jobs[index][0], jobs[index][1]));
                index++;
            }
            if(queue.size() > 0) {
                Disk now = queue.poll();
                int process = time + now.process - now.request;
                answer += process;
                time = time + now.process;
            } else {
                time = jobs[index][0] + jobs[index][1];
                answer += jobs[index][1];
                index++;
            }
            count++;
        }

        return answer/jobs.length;
    }
    class Disk implements Comparable<Disk>{
        int request;
        int process;

        public Disk(int request, int process) {
            this.request = request;
            this.process = process;
        }

        @Override
        public int compareTo(Disk o) {
            return this.process - o.process;
        }
    }
}
```



> ### 오답

```java
import java.util.*;

class Solution {
    public int solution(int[][] jobs) {
        int answer = 0;

        int second = 0;     // 작업 시작 시간
        int index = 0;
        int count = 0;
        Queue<Integer> queue = new PriorityQueue<>();

        Arrays.sort(jobs, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[0] - o2[0];
            }
        });

        while(count != jobs.length){
            // 시작 가능한 작업들 우선 순위 큐에 담기
            while(index != jobs.length && second >= jobs[index][0]){
                queue.add(jobs[index][1]-jobs[index][0]);
                index++;
            }
            if(queue.size() > 0) {
                int process = second + queue.poll();
                answer += process;
                second = answer;
            } else {
                second = jobs[index][0] + jobs[index][1];
                answer += jobs[index][1];
                index++;
            }
            count++;
        }

        return answer/jobs.length;
    }
}
```

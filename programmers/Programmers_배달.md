# [Programmers] 배달



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/

<br>

> ### solution

```java
import java.util.*;

class Solution {
    public int solution(int N, int[][] road, int K) {
        int answer = 0;

        List<Town>[] towns = new ArrayList[N+1];    // 연관도시
        int[] minimum = new int[N+1];       // 각 도시에 도착하는 최소 시간

        // init
        Arrays.fill(minimum, 500001);     // 최대값이 500000
        minimum[1] = 0;     // 자기 자신

        for(int i=0; i<=N; i++){
            towns[i] = new ArrayList<>();
        }
        // 경로 세팅
        for(int i=0; i< road.length; i++){
            int a = road[i][0];
            int b = road[i][1];
            int h = road[i][2];

            towns[a].add(new Town(b, h));
            towns[b].add(new Town(a, h));
        }

        Queue<Town> queue = new PriorityQueue<>();
        queue.add(new Town(1, 0));
        while(!queue.isEmpty()){
            Town now = queue.poll();

            int num = now.num;
            int hour = now.hour;

            if(minimum[num] >= hour) {       // 최소값 X

                // 연관 도시
                for(int i=0; i<towns[num].size(); i++){
                    Town next = towns[num].get(i);
                    int nextNum = next.num;
                    int nextHour = hour+ next.hour;

                    if(minimum[nextNum] > nextHour){
                        minimum[nextNum] = nextHour;
                        queue.add(new Town(nextNum, nextHour));
                    }
                }
            }
        }

        for(int i=1; i<=N; i++){
            if(minimum[i] <= K) answer++;
        }
        return answer;
    }

    class Town implements Comparable<Town>{
        int num;
        int hour;

        public Town(int num, int hour) {
            this.num = num;
            this.hour = hour;
        }

        @Override
        public int compareTo(Town o) {
            return hour - o.hour;
        }
    }
}
```

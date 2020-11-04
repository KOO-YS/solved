# [Programmers] 방문 길이

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/49994



> ### Solution

```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.HashSet;
import java.util.Set;

class Solution {
    public int solution(String dirs) {
        int answer = 0;

        char[] directions = dirs.toCharArray();
        // 현재 좌표
        int[] now = new int[2];

        Set<String> wayStr = new HashSet<>();

        for(char d : directions){
            int[] nextDir = move(d);
            int[] next = {now[0]+nextDir[0], now[1]+nextDir[1]};

            // 범위를 벗어나면 무효
            boolean boundary = (-5 <= next[0] && next[0] <= 5 && -5 <= next[1] && next[1]<= 5);
            if(!boundary) continue;

            int[][] way = {{now[0], now[1]}, {next[0], next[1]}};
            now = next;

            // 정렬한 뒤 저장
            Arrays.sort(way, new Comparator<int[]>() {
                @Override
                public int compare(int[] o1, int[] o2) {
                    if(o1[0]-o2[0] == 0){
                        return o1[1]-o2[1];
                    }else return o1[0]-o2[0];
                }
            });

            
            // 정렬된 순서대로 문자열로 만들기
            StringBuilder str = new StringBuilder();
            str.append(way[0][0]);
            str.append(way[0][1]);
            str.append(way[1][0]);
            str.append(way[1][1]);

            // 같은 문자열 -> 같은 경로를 지난다
            if(!wayStr.contains(str.toString())){
                wayStr.add(str.toString());
                answer++;
            }
        }
        return answer;
    }
    public int[] move(char ch){
        int[] next = new int[2];

        switch (ch){
            case 'U':
                next[1] = 1;
                break;
            case 'D':
                next[1] = -1;
                break;
            case 'R':
                next[0] = 1;
                break;
            case 'L':
                next[0] = -1;
                break;
        }
        return next;
    }
}
```

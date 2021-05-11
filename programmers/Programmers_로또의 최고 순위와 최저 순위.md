# [Programmers] 로또의 최고 순위와 최저 순위

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/77484



> ### Solution

```java
import java.util.*;
2
​
3
class Solution {
4
    public int[] solution(int[] lottos, int[] win_nums) {
5
        int[] answer = new int[2];
6
        
7
        int min = Integer.MAX_VALUE;
8
        int max = 0;
9
        
10
        Arrays.sort(lottos);
11
        Arrays.sort(win_nums);
12
        
13
        int index = 0;
14
        // 0의 개수 카운트
15
        while(lottos[index] ==0){
16
            index ++;
17
        }
18
        max = index;
19
        
20
        // 
21
        
22
        return answer;
23
    }
24
}

```

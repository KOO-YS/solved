# [Programmers] 로또의 최고 순위와 최저 순위

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/77484



> ### Solution

```java
import java.util.*;

class Solution {
    public int[] solution(int[] lottos, int[] win_nums) {
        int[] answer = new int[2];
        
        int min = 0;
        int max = 0;
        
        Arrays.sort(lottos);
        Arrays.sort(win_nums);
        
        int index = 0;
        // 0의 개수 카운트
        while(index < lottos.length && lottos[index] == 0){
            index++;
        }
        
        if(index != 0){       // 0이 한 개 이상 존재한다면?
            max = index;
            index -= 1; 
        }
        int temp = 0;
        for(int i=index; i<lottos.length; i++){
            for(int j = temp; j<win_nums.length; j++){
                // 일치하는 숫자 존재
                if(lottos[i] == win_nums[j]){
                    min ++;
                    temp ++;
                    break;
                }
            }
        }
        max += min;
        answer[0] = getRank(max);       // 최고 순위
        answer[1] = getRank(min);       // 최저 순위
        
        return answer;
    }
    /**
    * 순위 측정
    */
    public int getRank(int count){
        int rank = 7 - count;
        if(rank > 5) return 6;
        return rank;
    }
}

```

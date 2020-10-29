# [Programmers] 영어 끝말잇기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12981

> ### Solution

```java
import java.util.*;

class Solution {
    public int[] solution(int n, String[] words) {
        int[] answer = {0, 0};
        int turn = 1;
        int count = 1;
        Set<String> used = new HashSet<>();
        char last = words[0].charAt(0);
        for(String w : words){
            // 끝말이 이어져있는지 확인
            if(w.charAt(0) == last){
                // 이미 사용된 단어인지 확인
                if(used.contains(w)){
                    answer[0] = (turn%n == 0)? n : turn%n;
                    answer[1] = (count%n == 0)? count/n : (count/n+1);
                    return answer;
                } else {
                    last = w.charAt(w.length()-1);
                    used.add(w);
                }

            } else {
                answer[0] = (turn%n == 0)? n : turn%n;
                answer[1] = (count%n == 0)? count/n : (count/n+1);
                return answer;
            }
            turn++;
            count++;
        }

        return answer;
    }
}
```


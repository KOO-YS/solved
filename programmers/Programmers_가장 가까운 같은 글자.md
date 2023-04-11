# [Programmers] 가장 가까운 같은 글자



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/142086

> ### Solution

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public int[] solution(String s) {
        int[] answer = new int[s.length()];

        Map<Character, Integer> letters = new HashMap<>();

        for (int i=0; i<s.length(); i++) {
            char ch = s.charAt(i);
            if (letters.containsKey(ch)) {
                answer[i] = i - letters.get(ch);
            } else {
                answer[i] = -1;
            }
            letters.put(ch, i);
        }

        return answer;
    }
}
```


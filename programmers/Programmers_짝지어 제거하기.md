# [Programmers] 짝지어 제거하기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12973

> ### Solution

```java
import java.util.*;

class Solution
{
    public int solution(String s)
    {
        // 문자열의 길이가 홀수일 경우, 모두 제거할 수 없다
        if(s.length() %2 == 1) return 0;

        Stack<Character> pairs = new Stack<>();
        for(Character c : s.toCharArray()){
            if(pairs.size() == 0){
                pairs.push(c);
            } else {
                // 앞 뒤 문자가 같다면 제거
                if (pairs.peek() == c) pairs.pop();
                else pairs.push(c);
            }
        }

        return pairs.size() == 0 ? 1 : 0;
    }
}
```


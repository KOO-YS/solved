# [Programmers] 올바른 괄호

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12909



> ### Solution

```java
import java.util.*;

class Solution {
    boolean solution(String s) {
        char[] brackets = s.toCharArray();
        Stack<Character> pairs = new Stack<>();
        for(char b : brackets){
            if(b == '('){
                pairs.add(b);       // 아무값이나 들어가도...
            } else {
                if(!pairs.isEmpty()) {
                    pairs.pop();
                } else return false;
            }
        }
        if(pairs.isEmpty()) return true;
        return false;
    }
}
```


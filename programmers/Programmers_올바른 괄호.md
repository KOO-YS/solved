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



<u>*점수 +2 여서 다르게 풀어봤음에도 추가 점수는 받지 못했다.*</u>

```java
import java.util.*;

// Stack & Count
class Solution {
    boolean solution(String s) {
        char[] brackets = s.toCharArray();
        // Stack<Character> pairs = new Stack<>();
        int open = 0;
        for(char b : brackets){
            if(b == '('){
                open++;
                // pairs.add(b);       // 아무값이나 들어가도...
            } else {
                if(open>0){
                    open--;
                } else return false;
                // if(!pairs.isEmpty()) {
                    // pairs.pop();
                // } else return false;
            }
        }
        if(open == 0) return true;
        
        // if(pairs.isEmpty()) return true;
        return false;
    }
}
```
# [Programmers] 괄호 회전하기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/76502
>



> ### Solution

```java
import java.util.*;

class Solution {
    public int solution(String s) {
        int answer = 0;
        int count = s.length();

        Queue<Character> queue = new LinkedList<>();
        for(char ch : s.toCharArray()){
            queue.add(ch);
        }
        while(count-- > 0){

            Stack<Character> stack = new Stack<>();
            int length = queue.size();


            Queue<Character> temp = new LinkedList<>();
            temp.addAll(queue);

            while(length-- > 0){
                char now = temp.peek();

                temp.add(temp.poll());
                if(now == '(' || now == '[' || now == '{'){
                    stack.add(now);
                } else if(stack.size() > 0 && (now == ')' || now == ']' || now == '}')) {
                    char peek = stack.peek();
                    if(peek == '(' && now == ')') stack.pop();
                    else if(peek == '[' && now == ']') stack.pop();
                    else if(peek == '{' && now == '}') stack.pop();
                    else break;
                } else break;
            }
            if(length == -1 && stack.size() == 0) answer++;
            queue.add(queue.poll());
        }
        return answer;
    }
}
```


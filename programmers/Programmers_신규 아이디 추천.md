# [Programmers] 신규 아이디 추천

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/72410



> ### Solution (1차 시도)

```java

import java.util.Deque;
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    public String solution(String new_id) {
        StringBuilder result = new StringBuilder();

        Deque<Character> temp = new LinkedList<>();
        Queue<Character> test = new LinkedList<>();

        for(char c : new_id.toCharArray()){
            // 유효한 문자만 저장
            if((c = isValidChar(c)) != ' ') {
                test.add(c);
            }
        }
        if(test.size() == 0) return "aaa";

        char last = test.poll();

        while(!test.isEmpty()){
            if(last == '.' && test.peek() == '.'){
                test.poll();
                continue;
            }
            temp.add(last);
            if(test.size() == 1 && test.peek() != '.'){
                temp.add(test.poll());
            } else if(!test.isEmpty()) {
                last = test.poll();
            }

        }

        temp = qwerty(temp);

        while(temp.size() > 15){
            temp.pollLast();
        }
        while(temp.size() < 3 && temp.size() > 0){
            temp.addLast(temp.peekLast());
        }

        temp = qwerty(temp);

        if(temp.isEmpty()) return "aaa";
        while(!temp.isEmpty()){
            result.append(temp.poll());
        }

        return result.toString();
    }

    private Deque<Character> qwerty(Deque<Character> temp) {
        boolean check1;
        boolean check2;
        while(!temp.isEmpty()){
            check1 = false;
            check2 = false;

            if(temp.peekFirst() == '.'){
                temp.pollFirst();
            } else check1 = true;
            if(!temp.isEmpty() && temp.peekLast() == '.'){
                temp.pollLast();
            } else check2 = true;

            if(check1 && check2) {
                break;
            }
        }

        return temp;
    }

    private char isValidChar(char ch){
        if((ch == '-') || (ch == '_') || (ch == '.')) return ch;
        else if(ch >= 'a' && ch <= 'z') return ch;
        else if(ch >= '0' && ch <= '9') return ch;
        else if(ch >= 'A' && ch <= 'Z') return (char)(ch+32);
        return ' ';     // 나머지
    }
}
```


# [Programmers] 괄호 변환



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/60058

> ### Solution

```java
import java.util.*;

class Solution {
    public String solution(String p) {
        StringBuilder answer = new StringBuilder();
        StringBuilder temp;

        // 다시 돌아올 지점

        while(p.length() != 0){

            int cut = 0;        // 분리 기준 인덱스
            String u = p.substring(0, cut = indexOfBalanced(p));
            String v = p.substring(cut);

            if (!isCorrectBrackets(u)) {
                // 올바른 괄호 문자열이 아니라면?
                temp = new StringBuilder("(");
                temp.append(solution(v)).append(")");

                u = u.substring(1, u.length()-1);
                for(int i=0; i<u.length(); i++){
                    if(u.charAt(i) == '(') temp.append(")");
                    else temp.append("(");
                }
                answer.append(temp);
                return answer.toString();
            } else {
                // 올바른 괄호 문자열이라면?
                answer.append(u);
                // v에 대해 진행
                p = v;
            }
        }
        return answer.toString();
    }
    /**
     * "균형잡힌 괄호 문자열 체크"
     * 괄호 개수가 균형잡혀 있을 때의 문자열의 크기 반환
     */
    public int indexOfBalanced(String p){
        int left = 0;
        int right = 0;

        for(char ch : p.toCharArray()){
            if(ch == '(') left++;
            else if(ch == ')') right++;

            if(left == right) break;
        }

        return (left + right);
    }

    /**
     * " 올바른 괄호 문자열 체크 "
     */
    public boolean isCorrectBrackets(String p){
        Stack<Integer> brackets = new Stack<>();
        for(char ch : p.toCharArray()){
            if(ch == '(') brackets.push(0);
            else if(ch == ')') {
                if(brackets.isEmpty()) return false;
                brackets.pop();
            }
        }
        return brackets.isEmpty();
    }
}
```


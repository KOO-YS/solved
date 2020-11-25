# [Programmers] JadenCase 문자열 만들기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12951

> ### Solution

```java
import java.util.*;

class Solution {
    public String solution(String s) {
        StringBuilder answer = new StringBuilder();
        StringTokenizer token = new StringTokenizer(s, " ", true);
        while(token.hasMoreTokens()){
            String temp = token.nextToken();
            temp = temp.toLowerCase();
            if(temp.charAt(0)>='a' && temp.charAt(0) <='z'){
                answer.append((char)(temp.charAt(0)-32));
                answer.append(temp.substring(1));
            } else {
                answer.append(temp);
            }
        }
        return answer.toString();
    }
}
```



*<u>`a 999    for the last week` 같이 공백이 여러개 있는 문자열일때, 공백의 크기를 그대로 반환해야한다</u>* 


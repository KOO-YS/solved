# [Programmers] 문자열 나누기 



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/140108?language=java

> ### Solution

```java

class Solution {
    public int solution(String s) {
        int answer = 0;
        
        while (s.length() < 0) {
            s = splitStr(s);    
            answer ++;
        }
        
        return answer;
    }
    
    String splitStr(String str) {
        char x = str.charAt(0);
        int same = 0;
        int different = 0; 
        for (int i=1; i<str.length(); i++) {
            if (str.charAt(i) == x)
                same ++;
            else 
                different ++;
            
            if ( same == different ) {
                str = str.substring(i, str.length());
                break;
            }
        }
        return str;
    }
}
```


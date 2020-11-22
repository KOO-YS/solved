# [Programmers] 가장 긴 팰린드롬



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12904

> ### Solution

```java
class Solution
{
    public int solution(String s){
        int answer = 1;
        if(s.length() == 1) return answer;
        for(int i = 1; i<s.length(); i++){
            int c = 1;
            int c2 = 1;
            // 연속된 문자열 최대가 홀수일경우
            while(i-c >= 0 && i+c<s.length()){
                if(s.charAt(i-c) != s.charAt(i+c)) break;
                c++;

            }
            // 짝수일 경우
            while(i-c2+1 >= 0 && i+c2<s.length()){
                if(s.charAt(i-c2+1) != s.charAt(i+c2)) break;
                c2++;
            }
            answer =  Math.max(answer, (c-1)*2 + 1);
            answer =  Math.max(answer, (c2-1)*2);

        }
        return answer;
    }
}
```


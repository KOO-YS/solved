# [Programmers] 3진수 temp

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/...



> ### Solution

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        StringBuilder result = new StringBuilder();
        while(n>0){
            result.append(n%3);
            n = n/3;
        }
        char[] temp = result.toString().toCharArray();
        int mul = 1;
        for(int i=temp.length-1; i>=0; i--){
            answer += (temp[i]-48)*mul;
            mul *= 3;
        }

        return answer;
    }
}
```


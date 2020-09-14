# [Programmers] 124 나라의 숫자

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12899



> ### Solution

```java
class Solution {
    /**
     *  x mod 3 의 값이
     *  각 [x]일때, 변환값
     *   -> 0 :: 4
     *   -> 1 :: 1
     *   -> 2 :: 2
     */
    public String solution(int n) {
        StringBuilder answer = new StringBuilder();

        int[] convert = { 4, 1, 2 };

        int quotient = 0;       // 몫
        int remainder = 0;      // 나머지

        while(n>0){
            quotient = n/3;
            remainder =  n%3;
            answer.insert(0, convert[remainder]);

            if(remainder == 0 & quotient>0) quotient--;
            n = quotient;
        }
        return answer.toString();
    }
}
```


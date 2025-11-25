# [Programmers] 분수의 덧셈

> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/120808



> ### Solution

```java
class Solution {
    public int[] solution(int numer1, int denom1, int numer2, int denom2) {
        // 각 분모의 값으로 곱해서 더하기
        int numer = numer1 * denom2 + numer2 * denom1;
        int denom = denom1 * denom2;
        
        // 최대공약수로 나누기
        int gcd = gcd(numer, denom);
        
        numer = numer / gcd;
        denom = denom / gcd;
        
        return new int[] {numer, denom};
    }
    
    public int gcd(int a, int b) {
        if (b == 0)
            return a;
        
        return gcd(b, a%b);
    }
}
```


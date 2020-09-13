# [Programmers] 피보나치 수

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12945



> ### Solution

```java
import java.math.BigInteger;

class Solution {
    public int solution(int n) {

        BigInteger answer = fibonacci(n);

        BigInteger mod = new BigInteger("1234567"); 
        return Integer.parseInt(answer.mod(mod).toString());
    }
    
    public BigInteger fibonacci(int n){

        BigInteger[] memoization = new BigInteger[n+1];

        memoization[0] = BigInteger.ZERO;
        memoization[1] = BigInteger.ONE;

        for(int i=2; i<=n; i++){
            memoization[i] = memoization[i-1].add(memoization[i-2]);
        }
        return memoization[n];
    }
}
```


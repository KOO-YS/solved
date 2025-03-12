# [Programmers] 시소 짝꿍



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/152996

> ### Solution
```java
```


> ### 실패 : 시간 초과
```java
class Solution {
    public long solution(int[] weights) {
        long count = 0;

        for (int i = 0; i < weights.length; i++) {
            for (int j = i + 1; j < weights.length; j++) {
                if (isSeesawPair(weights[i], weights[j])) {
                    count++;
                }
            }
        }
        return count;
    }

    private boolean isSeesawPair(int w1, int w2) {
        int gcd = gcd(Math.max(w1, w2), Math.min(w1, w2));
        return (w1 % gcd == 0 && w2 % gcd == 0) && (w1 / gcd <= 4 && w2 / gcd <= 4);
    }

    /**
     * 최대 공약수 계산 (유클리드 호제법)
     */
    private int gcd(int a, int b) {
        return b == 0 ? a : gcd(b, a % b);
    }
}
```


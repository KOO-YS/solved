# [Programmers] N개의 최소공배수



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12953



> ### Solution

```java
import java.util.*;
class Solution {
    public int solution(int[] arr) {
        int answer = 0;

        answer = arr[0];
        for(int i=1; i<arr.length; i++){
            // 두 수를 뽑아 최소 공배수 계산
            answer = lcm(answer, arr[i]);
        }

        return answer;	// 모든 수를 다 돌면서 최소공배수 구한 값
    }

    // 최소 공배수
    public int lcm(int a, int b){
        return (a*b)/gcd(a,b);
    }
    // 최대 공약수
    public int gcd(int a, int b){
        if(b == 0) return a;
        return gcd(b, a%b);
    }
}
```


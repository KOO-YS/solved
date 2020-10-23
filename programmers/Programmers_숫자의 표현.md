# [Programmers] 숫자의 표현



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/12924



> ### Solution

```java
class Solution {
    public int solution(int n) {
        int answer = 1;
        int fivo = 1;

        for(int i=2; i<=n/2; i++){
            fibo += i;
            if(fibo > n) break;
            if(((n-fibo)%i) == 0) answer++;
        }

        return answer;
    }
}
```



> #### 풀이 설명
>
> 15를 두 개의 연속된 숫자로 표현
>
> 7 + 8  		 -> 	(6 + **1**) + (6 + **2**) 					-> 	**6*2 + (1 + 2)**
>
> 
>
> 15를 세 개의 연속된 숫자로 표현
>
> 4 + 5 + 6 	->	(3 + **1**) + (3 + **2**) + (3 + **3**) 	-> 	**3*3 + (1 + 2 + 3)**
>
> 
>
> #### n 에서  i까지 피보나치 합 (1 + 2 + 3 + ...+ i)을 뺀 후,  n-fibo(i)의 결과가 i로 완벽히 나누어 진다면 ? 
>
> #### i개의 연속된 수로 n을 완성할 수 있다 
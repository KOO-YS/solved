# [Programmers] 입국심사



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/43238
>



> ### Solution
>
> <br>
>
> ##### 참고 블로그
>
> https://velog.io/@ollabu3/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EC%9E%85%EA%B5%AD%EC%8B%AC%EC%82%AC
>
> <br>
>
>  6명, 심사 시간 [7,10] 일 때
>
> - Max : 6명 * 10 = 60분
>   - 1번째 심사관 : 60분/7분 = 8명 심사 가능
>   - 2번째 심사관 : 60분/10분 = 6명 심사 가능
>   - 총 8+6 = 14명 심사 가능
>   -  
>
> <br>

```java

```

<br>

<br>

> ### <del>오답</del>

```java
import java.util.*;

class Solution {
    public long solution(int n, int[] times) {
        // 심사 처리가 빠른 순으로 정렬
        Arrays.sort(times);

        long[] taken = new long[times.length];

        while(n > 0){
            // i == 0
            n--;
            taken[0] += times[0];
            if(n == 0) break;

            for(int i=1; i<times.length; i++){
                for(int j=0; j<i; j++){
                    if(taken[j]+times[j] >= taken[i]+times[i]){
                        taken[i] += times[i];
                    } else break;
                    n--;
                }
            }
        }

        Arrays.sort(taken);
        return taken[taken.length-1];
    }
}
```


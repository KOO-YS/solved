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
> https://yubh1017.tistory.com/30
>
> https://velog.io/@ollabu3/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EC%9E%85%EA%B5%AD%EC%8B%AC%EC%82%AC
>
> <br>
>
> 6명, 심사 시간 [7,10] 일 때
>
> - ##### Max 시간 : 6명 * 10 = 60분
>
>   - 1번째 심사관 : 60분/7분 = 8명 심사 가능
>   - 2번째 심사관 : 60분/10분 = 6명 심사 가능
>   - 총 8+6 = 14명 심사 가능 -> **실제로 검사해야하는 6명보다 많다**
>
> - ##### 시간을 중간으로 줄인다 -> (0+60)/2 = 30분
>
>   -  1번째 심사관 : 30분/7분 = 4명 심사 가능
>   - 2번째 심사관 : 30분/10분 = 3명 심사 가능
>   - 총 4+3 = 7명 심사 가능 -> **실제로 검사해야하는 6명보다 많다**
>
> - ##### 끝 시간을 앞당긴다 ( end = 30-1 ) -> (0+29)/2 = 14분
>
>   - 1번째 심사관 : 14분/7분 = 2명 심사 가능
>   - 2번째 심사관 : 14분/10분 = 1명 심사 가능
>   - 총 2+1 = 3명 심사 가능 -> **실제로 검사해야하는 6명보다 적다**
>   
> - ##### 시작 시간을 늦춘다 (start = 14 + 1 ) -> (15+29)/2 = 22분
>
>   - 1번째 심사관 : 22분/7분 = 3명 심사 가능
>   - 2번째 심사관 : 22분/10분 = 2명 심사 가능
>   - 총 3+2 = 5명 심사 가능 -> **실제로 검사해야하는 6명보다 적다**
>
> - ##### 시작 시간을 늦춘다 ( start = 22 + 1 ) -> (23+29)/2 = 26분
>
>   - 1번째 심사관 : 26분/7분 = 3명 심사 가능
>   - 2번째 심사관 : 26분/10분 = 2명 심사 가능
>   - 총 3+2 = 5명 심사 가능 -> **실제로 검사해야하는 5명보다 적다**
>
> - ##### 시작 시간을 늦춘다 (start = 26 + 1) -> (27+29)/2 = 28분
>
>   - 1번째 심사관 : 28분/7분 = 4명 심사 가능
>   - 2번째 심사관 : 28분/10분 = 2명 심사 가능
>   - 총 4+2 = 6명 심사 가능 -> **실제로 검사해야하는 6명 일치**
>
> - ##### 답은 28분
>
> <br>

```java
import java.util.*;

// 입국심사
class Solution {
    public long solution(int n, int[] times) {
        long answer = Long.MAX_VALUE;       // 최솟값을 구하기 위한 초기화

        Arrays.sort(times);

        long start = 0;
        long end = Long.MAX_VALUE;
        long mid;
        long count;

        while (start<= end){
            mid = (start + end)/2;
            count = 0;

            // mid(중간 시간)가 기준
            for(int t : times){
                count += mid/t;         // mid동안 각 심사원이 검사할 수있는 사람 수 ++

                if(count >= n) break;   // 검사해야 할 인원보다 많으면 중지
            }
            if(n <= count){     // 검사 인원이 초과하므로 끝 경계를 낮춰야함
                answer = Math.min(answer, mid);
                end = mid - 1;
            } else {            // 검사 인원이 부족하므로 시작 경계를 높여야함
                start = mid+1;
            }
        }

        return answer;
    }
}
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

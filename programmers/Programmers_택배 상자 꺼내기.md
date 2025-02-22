# [Programmers] 택배 상자 꺼내기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/389478

> ### Solution

```java
```

### 오답 3

```java
class Solution {
    public int solution(int n, int w, int num) {
        int answer = 0;

        // n과 num이 위치한 층 계산
        int nRow = (n - 1) / w; 
        int numRow = (num - 1) / w; 
        
        // 꺼내야 할 상자 개수 (위에 있는 모든 상자 포함)
        answer += (nRow - numRow + 1);

        // 각 행에서의 실제 열 위치 계산
        int nCol = (nRow % 2 == 0) ? (n - 1) % w : (w - 1) - ((n - 1) % w);
        int numCol = (numRow % 2 == 0) ? (num - 1) % w : (w - 1) - ((num - 1) % w);
        
        // 같은 줄인 경우, num이 n보다 오른쪽에 있으면 하나 덜 꺼내야 함
        if (numRow == nRow && numCol > nCol) {
            answer--;
        }

        return answer;
    }
}
```

### 오답 2

```java
class Solution {
    public int solution(int n, int w, int num) {
        int answer = 0;

        int nRow = n/w + ((n % w ==0)? 0 : 1);
        int numRow = num/w + ((num % w ==0)? 0 : 1);

        answer += (nRow - (numRow - 1));

        if (w == 1)
            return answer;
        
        int nCol = n%w;
        int numCol = num%w;
        
        // 짝수 줄이라면 <- 이동 
        if ((nRow % 2 == 0)) {
            if ((numRow % 2 == 0)) {
                if (numCol > nCol) {
                    answer --;
                }
            }
            else
                if ((nCol + numCol) < w) {
                    answer --;
                }
        } 
        // 홀수 줄이라면 -> 이동
        else {
            if (nCol < numCol)
                answer --;
        }
        return answer;
    }
}
```


### 오답 1
```java
class Solution {
    public int solution(int n, int w, int num) {
        int answer = 1;     // num 번 상자 자체

        int nRow = n/w + ((n % w ==0)? 0 : 1);
        int numRow = num/w + ((num % w ==0)? 0 : 1);

        answer += (nRow - numRow);

        int nCol = (nRow % 2 == 0)? (w - (n%w - 1)) : n%w;
        int numCol = (numRow % 2 == 0)? (w - (num%w - 1)) : num%w;

        if (numCol <= nCol)
            answer ++;

        return answer;
    }
}
```

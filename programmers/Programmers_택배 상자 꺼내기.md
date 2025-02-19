# [Programmers] 택배 상자 꺼내기



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/389478

> ### Solution

```java
```


### 오답
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

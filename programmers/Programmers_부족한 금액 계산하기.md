# [Programmers] 부족한 금액 계산하기



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/82612

<br>

> ### solution

```java
class Solution {
    public long solution(int price, int money, int count) {
        long answer = -1;
        int total = (price + count*price) * (count/2);

        if (count == 1)
            answer = price;
        else
            answer = total;
       answer -= money;

        if (answer  > 0) return answer;

        return 0;
    }
}
```

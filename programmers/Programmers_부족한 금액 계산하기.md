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
        long total = (long)(1 + count) * price *count / 2;
        answer = total - money;
        if (answer  > 0) return answer;

        return 0;
    }
}
```
줄이기
```java
class Solution {
    public long solution(int price, int money, int count) {
        long answer = (long)(1 + count) * price *count / 2 - money;
        return (answer  > 0)?  answer : 0;
    }
}
```

줄이기

```java
class Solution {
    public long solution(int price, int money, int count) {
        return Math.max((long)(1 + count) * price *count /2 - money, 0);
    }
}
```


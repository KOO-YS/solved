# [Programmers] 옹알이



> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/120956

> ### Solution

```java
class Solution {
    
    public final String[] possible = {"aya", "ye", "woo", "ma"};
    public final String[] impossible = {"ayaaya", "yeye", "woowoo", "mama"};

    public int solution(String[] babbling) {
        int count = 0;

        for (String b : babbling) {
            for (String i : impossible) {
                b = b.replace(i, "!");
            }
            for (String p : possible) {
                b = b.replace(p, "");
            }

            if (b.equals("")) count++;
        }

        return count;
    }
}
```


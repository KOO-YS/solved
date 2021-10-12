# [Programmers] 5주차_모음사전

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/84512

<br>

> ### solution

```java
class Solution {
    public int solution(String word) {
        int answer = 0;

        String vowel = "AEIOU";
        int[] gap = new int[]{781, 156, 31, 6, 1};

        int index;
        for (int i=0; i<word.length(); i++) {
            index = vowel.indexOf(word.charAt(i));
            answer += gap[i]*index + 1;
        }

        return answer;
    }
}
```

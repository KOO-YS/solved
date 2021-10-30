# [Programmers] 숫자 문자열과 영단어

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/81301

<br>

> ### solution

```java
class Solution {
    public static String[] intNum = {"0", "1", "2", "3", "4", "5", "6", "7", "8", "9"};
    public static String[] strNum = {"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"};

    public int solution(String s) {
        for (int i=0; i<10; i++) {
            s = s.replaceAll(strNum[i], intNum[i]);
        }
        return Integer.parseInt(s);
    }
}
```

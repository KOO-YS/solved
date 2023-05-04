# [Programmers] 가장 큰 수



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/155652



> ### Solution

```java
public String solution(String s, String skip, int index) {
    String answer = "";

    int[] exception = new int[skip.length()];
    for (int i=0; i<skip.length(); i++) {
        exception[i] = skip.charAt(i) - 'a';
    }

    for (int i=0; i<s.length(); i++) {
        int alphabetInt = s.charAt(i) - 'a';

    }


    return answer;
}
```


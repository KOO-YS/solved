# [Programmers] 2 x n 타일링 



> ### Problem
>
> https://school.programmers.co.kr/learn/courses/30/lessons/159994?language=java

> ### Solution

```java
class Solution {
    public String solution(String[] cards1, String[] cards2, String[] goal) {

        int index1 = 0;
        int index2 = 0;

        try {
            for (String word : goal) {
                if (cards1.length > index1 && cards1[index1].equals(word))
                    index1 ++;
                else if (cards2.length > index2 && cards2[index2].equals(word))
                    index2 ++;
                else return "No";
            }
        } catch (ArrayIndexOutOfBoundsException e) {
            return "No";
        }
        return "Yes";
    }
}
```


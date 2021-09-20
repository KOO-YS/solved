# [Programmers] **상호평가**

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/83201

<br>

> ### solution

```java
class Solution {
    public String solution(int[][] scores) {
        StringBuilder answer = new StringBuilder();

        for (int i=0; i<scores.length; i++) {
            answer.append(setGrade(setScore(scores, i)));
        }

        return answer.toString();
    }

    public int setScore(int[][] scores, int num) {
        int own = scores[num][num];
        int count = 0;
        int max = Integer.MIN_VALUE;
        int min = Integer.MAX_VALUE;

        int sum = 0;

        for (int i=0; i<scores.length; i++) {
            int now = scores[num][i];

            if(now == own) count++;
            max = Math.max(max, now);
            min = Math.min(min, now);

        }
        if(max == own && count == 1) sum -= max;
        else if(min == own && count == 1) sum -= min;
        else sum 
        
    }

    public char setGrade(int average) {
        char result = 'F';
        int cut = 90;
        char grade = 'A';

        while(cut > 50) {
            if (average >= cut) {
                return grade;
            }
            cut -= 10;
            grade = (char) (grade+1);
        }
        return result;
    }
}
```

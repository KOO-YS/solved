# [Programmers] **상호평가**

> ### Problem
>
> https://programmers.co.kr/learn/courses/30/lessons/83201

<br>

> ### solution

```java
import java.util.*;

class Solution {
    
    public static int total;
    public static int[][] scores;
    public static boolean[] except;
    
    public String solution(int[][] input) {

        scores = input;
        total = scores.length;
        except = new boolean[total];

        StringBuilder answer = new StringBuilder();

        for (int i=0; i<total; i++) {
            answer.append(setGrade(setScore(i)));
        }

        return answer.toString();
    }

    public int setScore(int num) {
        int result = 0;

        int[] grading = new int[total];
        for (int i=0; i<total; i++) {
            grading[i] = scores[i][num];
            result += grading[i];
        }

        int own = scores[num][num];

        Arrays.sort(grading);
        if (grading[0] == own && grading[1] != own ||
            grading[total - 1] == own && grading[total - 2] != own) {
                result -= own;
                return result/(total-1);
        }
        return result/total;
    }

    public char setGrade(int average) {
        char result = 'F';
        int cut = 90;
        char grade = 'A';

        while(cut > 60) {       // til C
            if (average >= cut) {
                return grade;
            }
            cut -= 10;
            grade = (char) (grade+1);
        }
        // D
        cut -= 10;
        if(average >= cut) return 'D';
        // F
        return result;
    }
}
```

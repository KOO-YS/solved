# [BaekJoon#2822] 점수 계산



> ### Problem
>
> https://www.acmicpc.net/problem/2822



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int n = 8;
        int count = 5;
        int sum = 0;

        Quiz[] quizzes = new Quiz[n];

        for (int i=0; i<n; i++) {
            quizzes[i] = new Quiz(i+1, Integer.parseInt(br.readLine()));
        }

        Arrays.sort(quizzes);

        int[] includes =  new int[count];

        for (int i=0; i<count; i++) {
            sum += quizzes[i].grade;
            includes[i] = quizzes[i].index;
        }

        Arrays.sort(includes);

        for (int i=0; i<count; i++) {
            result.append(includes[i]).append(' ');
        }

        System.out.println(sum);
        System.out.println(result);
    }

    static class Quiz implements Comparable<Quiz> {
        int index;
        int grade;

        public Quiz(int index, int grade) {
            this.index = index;
            this.grade = grade;
        }

        @Override
        public int compareTo(Quiz o) {
            if (this.grade < o.grade)
                return 1;
            else if (this.grade > o.grade)
                return  -1;
            else return 0;
        }
    }
}
```


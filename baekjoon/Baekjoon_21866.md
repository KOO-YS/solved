# [BaekJoon#21866] 추첨을 통해 커피를 받자


> ### Problem
>
> https://www.acmicpc.net/problem/21866



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {


    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int[] max = { 100, 100, 200, 200, 300, 300, 400, 400, 500};
        int index = 0;
        int grade;
        int total = 0;
        while (tokenizer.hasMoreTokens()) {
            grade = Integer.parseInt(tokenizer.nextToken());
            if (grade > max[index]) {
                System.out.println("hacker");
                return;
            }
            total += grade;
            index ++;
        }
        if (total < 100)
            System.out.println("none");
        else
            System.out.println("draw");
    }
}
```

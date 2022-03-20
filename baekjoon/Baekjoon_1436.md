# [BaekJoon#1436] 영화감독 숌



> ### Problem
>
> https://www.acmicpc.net/problem/1436



> ### Solution


```java
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        int number = 666;
        int count = 1;

        while (count != N) {
            number++;

            if (String.valueOf(number).contains("666")) count++;
        }

        System.out.println(number);
    }
}
```

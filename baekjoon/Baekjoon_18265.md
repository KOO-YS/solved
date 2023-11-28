# [BaekJoon#18265] MooBuzz



> ### Problem
>
> https://www.acmicpc.net/problem/18265



> ### Solution


> ### Timeout
```java
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        int num = 1;
        int count = 1;

        while (count != N ) {
            num++;
            if (num % 3 != 0 && num % 5 != 0) {
                count++;
            }
        }
        System.out.println(num);
    }
}
```

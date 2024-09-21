# [BaekJoon#31655] International Dates



> ### Problem
>
> https://www.acmicpc.net/problem/31655



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine(), "/");

        String AA = tokenizer.nextToken();
        String BB = tokenizer.nextToken();
        String CCCC = tokenizer.nextToken();

        if (Integer.parseInt(AA) > 12)
            System.out.println("EU");
        else if (Integer.parseInt(BB) > 12)
            System.out.println("US");
        else
            System.out.println("either");
    }
}

```

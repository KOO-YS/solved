# [BaekJoon#10280] Pizza voting



> ### Problem
>
> https://www.acmicpc.net/problem/10280



> ### Wrong

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Main {


    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine());

        int n = Integer.parseInt(tokenizer.nextToken());
        int p = Integer.parseInt(tokenizer.nextToken());

        int turn = n / 3;
        for (int i=0; i<n; i++) {
            tokenizer = new StringTokenizer(br.readLine());
        }
        if (n < 3)
            System.out.println("NO");
        else {
            int answer = Math.abs((n - p) - p);
            if (answer <= turn)
                System.out.println("YES");
            else
                System.out.println("NO");
        }
    }
}
```

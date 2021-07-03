# [BaekJoon#2475] 검증수



> ### Problem
>
> https://www.acmicpc.net/problem/2475



> ### Solution

```java
import java.io.*;
import java.util.*;

class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer = new StringTokenizer(br.readLine(), " ");

        int sum = 0;
        int now;
        while(tokenizer.hasMoreTokens()) {
            now = Integer.parseInt(tokenizer.nextToken());
            sum += (now*now);
        }
        System.out.println(sum%10);
    }
}
```


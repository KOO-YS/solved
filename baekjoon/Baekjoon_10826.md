# [BaekJoon#10826] 피보나치 수 4



> ### Problem
>
> https://www.acmicpc.net/problem/10826



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.math.BigInteger;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());

        if (n == 0) {
            System.out.println(0);
        } else if (n == 1) {
            System.out.println(1);
        } else {
            BigInteger[] temp = new BigInteger[n + 1];

            temp[0] = BigInteger.ZERO;
            temp[1] = BigInteger.ONE;

            for (int i = 2; i <= n; i++) {
                temp[i] = temp[i - 2].add(temp[i - 1]);
            }
            System.out.println(temp[n]);
        }
    }
}
```

> ##### 무한대 범위를 가진 정수 : `BigInteger` 사용
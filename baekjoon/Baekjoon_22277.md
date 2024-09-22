# [BaekJoon#22277] Non-Integer Donuts



> ### Problem
>
> https://www.acmicpc.net/problem/22277



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.math.BigDecimal;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int late = 0;
        int N = Integer.parseInt(br.readLine());

        BigDecimal balance = new BigDecimal(br.readLine().replace("$", ""));

        for (int i=0; i<N; i++) {
            balance = balance.add(new BigDecimal(br.readLine().replace("$", "")));

            if ( balance.remainder(BigDecimal.ONE).compareTo(BigDecimal.ZERO) != 0 )
                late++;
        }

        System.out.println(late);
    }
}

```

### Wrong
- 0.1 을 계속해서 더했을 때 오차가 발생했다

### Tips
- Double 객체를 사용할 경우 부동소수점 오차가 발생할 수 있다.
- 부동소수점 오차 : 주로 IEEE 754 표준에 따라 숫자를 이진수로 표현하는 방식 때문에 발생하며, 실수 -> 이진수로 변환할 때 일부 소수점 이하 숫자를 정확하게 표현할 수 없기 때문에 발생

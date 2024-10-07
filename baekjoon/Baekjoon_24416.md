# [BaekJoon#24416] 알고리즘 수업 - 피보나치 수 1


> ### Problem
>
> https://www.acmicpc.net/problem/24416



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int n = Integer.parseInt(br.readLine());

        fib01Result = 0;
        fib02Result = 0;

        fib02Arr = new int[n+1];

        fib01(n);
        fib02(n);

        result.append(fib01Result).append(' ').append(fib02Result);

        System.out.println(result);
    }

    static int fib01Result;
    public static int fib01(int n) {
        if (n == 1 || n == 2) {
            fib01Result++;
            return 1;
        }
        return (fib01(n-1) + fib01(n-2));
    }

    static int fib02Result;
    static int[] fib02Arr;
    public static int fib02(int n) {

        if (n == 1 || n == 2) {
            fib02Arr[n] = 1;
        }
        for (int i=2; i<n; i++) {
            fib02Result++;
            fib02Arr[i] = fib02Arr[i-2] + fib02Arr[i-1];
        }
        return fib02Arr[n-1];
    }
}
```

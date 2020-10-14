# [BaekJoon#1788] 피보나치 수의 확장



> ### Problem
>
> https://www.acmicpc.net/problem/1788

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(br.readLine());
        boolean isMinus = false;
        if(Math.abs(n) <= 1) {
            System.out.println(Math.abs(n));
            System.out.println(Math.abs(n));
            return;
        }
        if(n<0){
            isMinus = true;
            n = Math.abs(n);
        }
        int[] dp = new int[n+1];
        dp[0] = 0;
        dp[1] = 1;

        for(int i=2; i<=n; i++){
            dp[i] = (dp[i-1] + dp[i-2])%1000000000;
        }

        if(isMinus && n%2 == 0) {
            System.out.println(-1);
        }
        else System.out.println(1);

        System.out.println(dp[n]);


    }
}

/*
음수 피보나치 -> 양수 피보나치와 같음 단, 2배수에 마이너스
* 0)    0
* -1)   1
* -2)   -1
* -3)   2
* -4)   -3
* -5)   5
* -6)   -8
*/
```

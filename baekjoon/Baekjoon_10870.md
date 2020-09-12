# [BaekJoon#10870] 피보나치 수 5  



> ### Problem
>
> https://www.acmicpc.net/problem/10870



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());

        memoization = new int[n+1];

        int answer = fibonacci02(n);
        System.out.println(answer);
    }

    // 단순 계산을 이용한 피보나치 구현
    public static int fibonacci01(int n){
        int sum = 1;
        int num1 =0, num2 = 0;
        for(int i=0; i<n-1; i++){
            num2 = sum;
            sum = num1 + num2;
            num1 = num2;
        }
        return sum;
    }
    public static int[] memoization;
    // 정석 -> but 시간 고려를 위한 memoization 필요
    public static int fibonacci02(int n){
        if(n == 0){
            return memoization[0] = 0;
        } else if(n == 1){
            return memoization[1] = 1;
        } else if(memoization[n] != 0){
            return memoization[n];
        }

        memoization[n] = fibonacci02(n-1) + fibonacci02(n-2);

        return memoization[n];
    }
}

```


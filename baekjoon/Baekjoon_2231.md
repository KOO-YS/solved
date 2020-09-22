# [BaekJoon#2231] 분해합



> ### Problem
>
> https://www.acmicpc.net/problem/2231



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());

        int answer = decomposition(N);

        System.out.println(answer);
    }
    // 분해합 반환
    public static int decomposition(int n){
        int constructor = 0;

        int start = n - ((int)Math.log10(n)+1)*9;
        int sum =0;
        int temp = 0;

        while(n > start){             // 분해합이 n보다 작을 경우까지 반복
            sum = start;            // 생성자와
            temp = start;
            while(temp>0){          // 생성자 각 자리수의 합
                sum += temp%10;
                temp /= 10;
            }
            constructor = start;
            start++;                // 다음 생성자 후보 검색

            if(sum == n) return constructor;

        }
        // 분해합이 존재하지 않음
        return 0;
    }
}
```

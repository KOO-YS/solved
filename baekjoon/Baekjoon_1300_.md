# [BaekJoon#1300] K번째 수



> ### Problem
>
> https://www.acmicpc.net/problem/1300

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(br.readLine());
        int K = Integer.parseInt(br.readLine());

        int answer = 0;

        int left = 1;
        int right = K;

        while(left <= right){
            int count = 0;
            int mid = (left + right)/2;
            for(int i=1; i<=N; i++){
                count += Math.min(mid/i, N);
            }
            if(count < K){
                left = mid +1;
            } else {
                answer = mid;
                right = mid -1;
            }
        }
        System.out.println(answer);
    }
}
```

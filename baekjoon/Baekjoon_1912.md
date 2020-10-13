# [BaekJoon#1912] 연속합



> ### Problem
>
> https://www.acmicpc.net/problem/1912

> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;
public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(br.readLine());
        int[] nums = new int[n];
        int[] dp = new int[n];
        StringTokenizer token = new StringTokenizer(br.readLine(), " ");
        for(int i=0; i<n; i++){
            nums[i] = Integer.parseInt(token.nextToken());
        }
        dp[0] = nums[0];
        for(int i=1; i<n; i++){
            dp[i] = Math.max(nums[i], dp[i-1]+nums[i]);
        }
        Arrays.sort(dp);
        System.out.println(dp[n-1]);
    }
}
```

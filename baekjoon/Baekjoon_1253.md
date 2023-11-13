# [BaekJoon#1253] 좋다



> ### Problem
>
> https://www.acmicpc.net/problem/1253



> ### Solution
>

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());

        int[] arr = new int[N];
        StringTokenizer token = new StringTokenizer(br.readLine());
        for (int i=0; i<N; i++) {
            arr[i] = Integer.parseInt(token.nextToken());
        }

        Arrays.sort(arr);       // 음수 포함...
        int count = 0;

        int start, end, sum;

        for (int i=0; i<N; i++) {
            start = 0;
            end = N-1;

            while (start < end) {
                sum = arr[start] + arr[end];
                if (sum == arr[i]) {
                    if (start == i)
                        start++;
                    else if (end == i)
                        end--;
                    else {
                        count++;
                        break;
                    }
                } else if (sum < arr[i]) {
                    start++;
                } else
                    end--;
            }
        }
        System.out.println(count);
    }

}
```

반례
```
3
-10 0 10
```
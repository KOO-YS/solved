# [BaekJoon#11053] 가장 긴 증가하는 부분 수열



> ### Problem
>
> https://www.acmicpc.net/problem/11053



> ### Solution

```java
import java.io.*;
import java.util.*;

// https://www.acmicpc.net/problem/4963
class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer token;

        int A = Integer.parseInt(br.readLine());
        int[] arr = new int[A];
        int[] longest = new int[A];

        token = new StringTokenizer(br.readLine());

        for(int i=0; i<A; i++){
            arr[i] = Integer.parseInt(token.nextToken());
        }

        longest[0] = 1;

        for (int i = 1; i < A; i++) {
            longest[i] = 1;
            for (int j = 0; j < i; j++) {
                if (arr[j] < arr[i] && longest[i] <= longest[j]) {
                    longest[i] = longest[j] + 1;
                }
            }
        }

        int length = 0;
        for (int i : longest) {
            length = Math.max(length, i);
        }

        System.out.println(length);
    }
}
```

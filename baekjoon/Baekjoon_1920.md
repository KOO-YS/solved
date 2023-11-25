# [BaekJoon#1920] 수 찾기



> ### Problem
>
> https://www.acmicpc.net/problem/1920



> ### Solution

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        String[] target = br.readLine().split(" ");
        Set<String> A = new HashSet<>();
        for(String num : target){
            A.add(num);
        }

        int M = Integer.parseInt(br.readLine());

        String[] compare = br.readLine().split(" ");
        for(String num : compare){
            if(A.contains(num)) result.append(1).append("\n");
            else result.append(0).append("\n");
        }
        System.out.print(result);
    }

}
```

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    static int[] arr;
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;

        int N = Integer.parseInt(br.readLine());

        arr = new int[N];
        tokenizer = new StringTokenizer(br.readLine(), " ");

        for (int i=0; i<N; i++) {
            arr[i] = Integer.parseInt(tokenizer.nextToken());
        }

        Arrays.sort(arr);

        int M = Integer.parseInt(br.readLine());
        tokenizer = new StringTokenizer(br.readLine(), " ");

        while (M-- > 0) {
            System.out.println(
                (exist(Integer.parseInt(tokenizer.nextToken())))? 1 : 0);
        }
    }

    static boolean exist(int value) {
        int start = 0;
        int end = arr.length - 1;

        while (start <= end) {
            int mid = (start + end) / 2;

            if (arr[mid] == value)
                return true;
            if (arr[mid] > value) {
                end = mid - 1;
            } else
                start = mid + 1;
        }

        return false;
    }

}

```

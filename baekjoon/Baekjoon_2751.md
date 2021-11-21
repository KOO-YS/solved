# [BaekJoon#2751] 수 정렬하기 2



> ### Problem
>
> https://www.acmicpc.net/problem/2751



> ### Solution

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.*;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder result = new StringBuilder();

        int N = Integer.parseInt(br.readLine());

        Queue<Integer> sorted = new LinkedList<>();
        while (N-- >0) {
            sorted.add(Integer.parseInt(br.readLine()));
        }

        sorted.stream().sorted().forEach(num -> result.append(num).append('\n'));

        System.out.println(result.toString());
    }
}
```
